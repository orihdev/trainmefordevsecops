pipeline {
    agent any


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
              app=docker.Build("oridevops2/snake:${env.BUILD_ID}")
                sh 'echo Build and Tag stage'
            }
        }
   stage('Image and Vulnerability Scan') {
            steps {
                sh ''
            }
   }
   stage('Post to Docker-Hub') {
            steps {
                sh ''
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
