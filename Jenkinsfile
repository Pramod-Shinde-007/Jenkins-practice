pipeline {
    agent any
    
    tools {
        maven 'M2_home'
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
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://44.211.204.1:8080')], contextPath: '/app', war: '**/*.war'
            }
        }
    }
}
