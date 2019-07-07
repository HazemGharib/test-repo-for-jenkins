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

                    }
                    environment {
                        
                    }
                    when {

                    }
                    steps {
                        
                    }
                }

                stage('Integration Tests') {
                    agent {

                    }
                    environment {
                        
                    }
                    when {

                    }
                    steps {
                        
                    }
                }

                stage('E2E Tests') {
                    agent {

                    }
                    environment {
                        
                    }
                    when {

                    }
                    steps {
                        
                    }
                }
            }
        }

        stage('Build release') {
            agent {

            }
            environment {
                
            }
            when {

            }
            steps {
                
            }
        }

        stage('Publish to Heroku') {
            agent {

            }
            environment {
                
            }
            when {

            }
            steps {
                
            }
        }
    }

  post {
    success {
      node("") {
          
      }
    }
    failure {
      node("") {
          
      }
    }
    cleanup {
      node("") {
        cleanWs deleteDirs: true
      }
    }
  }
}