pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('1221') // Use the provided ID for credentials
        GITHUB_REPO = 'https://github.com/NUCESFAST/scd-final-lab-exam-Saif1221Orakzai.git'
        DOCKER_IMAGE_AUTH = 'i211221/auth'
        DOCKER_IMAGE_CLASSROOMS = 'i211221/classrooms'
        DOCKER_IMAGE_CLIENT = 'i211221/client'
        DOCKER_IMAGE_EVENT_BUS = 'i211221/event-bus'
        DOCKER_IMAGE_POST = 'i211221/post'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: env.GITHUB_REPO
            }
        }

        stage('Build and Push Auth Image') {
            steps {
                script {
                    dir('Auth') {
                        sh 'docker build -t $DOCKER_IMAGE_AUTH .'
                        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                        sh 'docker push $DOCKER_IMAGE_AUTH'
                    }
                }
            }
        }

        stage('Build and Push Classrooms Image') {
            steps {
                script {
                    dir('Classrooms') {
                        sh 'docker build -t $DOCKER_IMAGE_CLASSROOMS .'
                        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                        sh 'docker push $DOCKER_IMAGE_CLASSROOMS'
                    }
                }
            }
        }

        stage('Build and Push Client Image') {
            steps {
                script {
                    dir('client') {
                        sh 'docker build -t $DOCKER_IMAGE_CLIENT .'
                        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                        sh 'docker push $DOCKER_IMAGE_CLIENT'
                    }
                }
            }
        }

        stage('Build and Push Event Bus Image') {
            steps {
                script {
                    dir('Event Bus') {
                        sh 'docker build -t $DOCKER_IMAGE_EVENT_BUS .'
                        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                        sh 'docker push $DOCKER_IMAGE_EVENT_BUS'
                    }
                }
            }
        }

        stage('Build and Push Post Image') {
            steps {
                script {
                    dir('Post') {
                        sh 'docker build -t $DOCKER_IMAGE_POST .'
                        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                        sh 'docker push $DOCKER_IMAGE_POST'
                    }
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
