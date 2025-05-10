// pipeline {
//     agent any

//     environment {
//         GIT_REPO_URL = 'https://github.com/Salhianis1/MERN-Frontend-Backend-docker-compose.git'
//         GIT_BRANCH = 'main' // or 'master' or any other branch
//     }

//     stages {
//         stage('Clone Repository') {
//             steps {
//                 echo "Cloning from ${env.GIT_REPO_URL}"
//                 git branch: "${env.GIT_BRANCH}", url: "${env.GIT_REPO_URL}"
//             }
//         }

//         stage('List Files') {
//             steps {
//                 sh 'ls -la'
//             }
//         }

//         pipeline {
//     agent any

//     environment {
//         GIT_REPO_URL = 'https://github.com/your-username/your-repository.git'
//         GIT_BRANCH = 'main'
//         SONARQUBE_ENV = 'MySonarQube' // This is the name of the SonarQube server configured in Jenkins
//     }

//     stages {
//         stage('Clone Repository') {
//             steps {
//                 echo "Cloning from ${env.GIT_REPO_URL}"
//                 git branch: "${env.GIT_BRANCH}", url: "${env.GIT_REPO_URL}"
//             }
//         }

//         stage('SonarQube Scan') {
//             steps {
//                 script {
//                     withSonarQubeEnv("${env.SONARQUBE_ENV}") {
//                         sh 'sonar-scanner'
//                     }
//                 }
//             }
//         }

//         stage('Quality Gate') {
//             steps {
//                 timeout(time: 1, unit: 'MINUTES') {
//                     waitForQualityGate abortPipeline: true
//                 }
//             }
//         }
//     }
// }

//     }
// }


pipeline {
    agent any

    environment {
        GIT_REPO_URL = 'https://github.com/Salhianis1/MERN-Frontend-Backend-docker-compose.git'
        GIT_BRANCH = 'main'
        SONARQUBE_ENV = 'SonarQube' // Name of SonarQube config in Jenkins
        SONAR_PROJECT_KEY = 'MERN-App'
    }

    stages {
        stage('Clone Repository') {
            steps {
                echo "Cloning from ${env.GIT_REPO_URL}"
                git branch: "${env.GIT_BRANCH}", url: "${env.GIT_REPO_URL}"
            }
        }

        stage('SonarQube Scan') {
            steps {
                script {
                    withCredentials([string(credentialsId: 'SonarQube-ID', variable: 'jenkins')]) {
                        withSonarQubeEnv("${env.SONARQUBE_ENV}") {
                            sh """
                                sonar-scanner \
                                -Dsonar.projectKey=${SONAR_PROJECT_KEY} \
                                -Dsonar.sources=. \
                                -Dsonar.token=${jenkins}
                            """
                        }
                    }
                }
            }
        }

        stage('Quality Gate') {
            steps {
                waitForQualityGate abortPipeline: true
            }
        }

    }
}


