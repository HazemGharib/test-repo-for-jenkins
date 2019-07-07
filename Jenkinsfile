properties([
    parameters(constructParameters(env.BRANCH_NAME))
])

def constructParameters(branchName) {
    def defaultParams = ([
        choice(
            name: 'BUILD_TYPE',
            choices: 'Alpha\nBeta\nStable',
            description: 'Select what type of build you want, Stable build will run all tests.'
        )
    ])
    switch (branchName) {
        case 'master':
            return defaultParams + ([
                string(
                    name: 'VERSION',
                    description: 'Package version to build.',
                    defaultValue: ''
                ),
                booleanParam(
                    name: 'HEROKU_RELEASE',
                    description: 'Package will be release on Heroku.',
                    defaultValue: false
                ),
                choice(
                    name: 'RELEASE_MAIL',
                    choices: 'Send\nIgnore',
                    description: 'Mail will be sent after build success or fail.',
                    defaultValue: 'Ignore'
                ),
            ])
        default:
            return defaultParams
    }
}

pipeline {
    agent none
    tools {
        jdk 'jdk8'
        maven 'M3'
    }

    environment {
        PROJECT_REPO_URL = 'git@github.com:HazemGharib/test-repo-for-jenkins.git'
    }

    stages {
        stage('Run automation') {
            parallel {
                stage('Unit Tests') {
                    agent {
                        node { label 'UT' }
                    }
                    // environment {
                        
                    // }
                    // when {

                    // }
                    steps {
                        sh 'echo "UT"'
                    }
                }

                stage('Integration Tests') {
                    agent {
                        node { label 'IT' }
                    }
                    // environment {
                        
                    // }
                    // when {

                    // }
                    steps {
                        sh 'echo "IT"'                        
                    }
                }

                stage('E2E Tests') {
                    agent {
                        node { label 'E2ET' }
                    }
                    // environment {
                        
                    // }
                    // when {

                    // }
                    steps {
                        sh 'echo "E2ET"'                        
                    }
                }
            }
        }

        stage('Build release') {
            agent {
                node { label 'UT' }
            }
            // environment {
                
            // }
            // when {

            // }
            steps {
                sh 'echo "Build release"' 
            }
        }

        stage('Publish to Heroku') {
            agent {
                node { label 'UT' }
            }
            // environment {
                
            // }
            // when {

            // }
            steps {
                sh 'echo "Publish to Heroku"' 
            }
        }
    }

  post {
    success {
      node("UT || IT || E2ET") {
          
      }
    }
    failure {
      node("UT || IT || E2ET") {
          
      }
    }
    cleanup {
      node("UT || IT || E2ET") {
        cleanWs deleteDirs: true
      }
    }
  }
}