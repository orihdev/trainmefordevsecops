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
                sh ''
            }
   }
   stage('Build and tag') {
            steps {
                sh ''
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
