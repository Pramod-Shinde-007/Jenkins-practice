pipeline {
    agent any
    
    tools {
        maven 'maven'
    }    

    stages {
        stage('git-checkout') {
            steps {
               checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Pramod-Shinde-007/Jenkins-practice.git']])
            }
        }
        stage('building-source-code') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('deploy-to-tomcat') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat9', path: '', url: 'http://13.232.253.140:8080')], contextPath: '/app', war: '**/*war'
            }
        }
    }
}
