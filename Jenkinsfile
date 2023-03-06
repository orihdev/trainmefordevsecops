pipeline {
    agent {
      label 'docker'
    }


    stages {
    stage('Git clone') {
        steps {
                checkout scmGit(branches: [[name: '*/email-notification']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/orihdev/trainmefordevsecops.git']])
        }
    }

   stage('SAST') {
            steps {
                sh 'echo SAST stage'
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
                docker.withRegistry('https://registry.hub.docker.com','Docker-hub-creds-orih') {
                    app.push("${env.BUILD_ID}")
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
