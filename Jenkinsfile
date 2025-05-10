pipeline {
    agent any

    environment {
        GIT_REPO_URL = 'https://github.com/Salhianis1/MERN-Frontend-Backend-docker-compose.git'
        GIT_BRANCH = 'main' // or 'master' or any other branch
    }

    stages {
        stage('Clone Repository') {
            steps {
                echo "Cloning from ${env.GIT_REPO_URL}"
                git branch: "${env.GIT_BRANCH}", url: "${env.GIT_REPO_URL}"
            }
        }

        stage('List Files') {
            steps {
                sh 'ls -la'
            }
        }
    }
}

