pipeline {
    agent any

    tools {
        jdk 'java 11'
        maven 'maven'
    }

    stages {
        stage('Git checkout') {
            steps {
                git branch: 'verion-1', url: 'https://github.com/ManojKRISHNAPPA/test-1.git'
            }
        }

        stage('Build & Package') {
            steps {
                // 'mvn clean install' automatically runs compile and test
                sh 'mvn clean install'
            }
        }

        stage('Building Docker Image') {
            steps {
                sh 'docker build -t mohamedsadiq9741:v1 .'
            }
        }

        stage('Containerization') {
            steps {
                sh '''
                    //docker stop c1 || true
                    //docker rm c1 || true
                    docker run -d --name c1 -p 9000:8081 mohamedsadiq9741:v1
                '''
            }
        }
    }
}
