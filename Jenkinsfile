pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                git url: 'https://github.com/dimitarilievv/CICD-Assignments', branch: 'main'
            }
        }
        stage('Build image') {
            steps {
                script {
                    app = docker.build("dimitarilievv/CICD-Assignments")
                }
            }
        }
        stage('Push image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                        app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
                        app.push("${env.BRANCH_NAME}-latest")
                    }
                }
            }
        }
    }
}
