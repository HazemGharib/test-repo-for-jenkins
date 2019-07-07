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

    environment {
        PROJECT_REPO_URL = 'git@github.com:HazemGharib/test-repo-for-jenkins.git'
    }

    stages {
        stage('Run automation') {
            parallel {
                stage('Unit Tests') {
                    agent {
                        node { label 'master' }
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
                        node { label 'master' }
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
                        node { label 'master' }
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
                node { label 'master' }
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
                node { label 'master' }
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
      node("master") {
          
      }
    }
    failure {
      node("master") {
          
      }
    }
    cleanup {
      node("master") {
        cleanWs deleteDirs: true
      }
    }
  }
}