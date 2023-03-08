pipeline {
    agent {
      label 'docker'
    }
    environment {
      SONAR_TOKEN=credentials('sonar-token')
    }
    
    stages {
    stage('Git clone') {
        steps {
                checkout scmGit(branches: [[name: '*/email-notification']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/orihdev/trainmefordevsecops.git']])
        }
    }

   stage('SAST') {
             environment {
                SONAR_SCANNER_VERSION = '4.7.0.2747'
                SONAR_SCANNER_HOME = "$HOME/.sonar/sonar-scanner-$SONAR_SCANNER_VERSION-linux"
                PATH = "$SONAR_SCANNER_HOME/bin:$PATH"
                SONAR_SCANNER_OPTS = '-server'
            }
            steps {
                sh 'curl --create-dirs -sSLo $HOME/.sonar/sonar-scanner.zip https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-$SONAR_SCANNER_VERSION-linux.zip'
                sh 'unzip -o $HOME/.sonar/sonar-scanner.zip -d $HOME/.sonar/'
                sh '''sonar-scanner \
                    -Dsonar.organization=orihdev \
                    -Dsonar.projectKey=orihdev_trainmefordevsecops \
                    -Dsonar.sources=. \
                    -Dsonar.host.url=https://sonarcloud.io'''
            }
   }
   stage('Build and tag') {
            steps {
              script{
              app = docker.build("oridevops2/snake:${env.BUILD_ID}")
              }
            }
        }
   stage('Image and Vulnerability Scan') {
            steps {
                sh ''
            }
   }
   stage('Post to Docker-Hub') {
            steps {
              script{
                docker.withRegistry('https://registry.hub.docker.com','Docker-hub-creds-orih') {
                    app.push("${env.BUILD_ID}")
                }
              }
            }
   }
    stage('Pull image server') {
            steps {
                sh ''
            }
    }
   stage('DAST') {
            steps {
                sh ''
            }
   }
   }
}
