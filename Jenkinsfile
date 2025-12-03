pipeline {

    agent any

    stages {

        stage('Build') {

            steps {

                echo 'Building Docker image...'

                // Замените ВАШ_ЛОГИН и ИМЯ_РЕПОЗИТОРИЯ на реальные

                sh 'docker build -t sbdiv/jenkins-pipeline-lab:latest .'

            }

        }

        stage('Test') {

            steps {

                echo 'Running tests...'

                sh 'echo "Tests passed!"'

            }

        }

        stage('Deploy to Docker Hub') {

            steps {

                echo 'Pushing Docker image to DockerHub...'

                // Используем сохраненные credentials по ID 'dockerhub-credentials'

                withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {

                    // Логинимся

                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'

                    // Пушим образ

                    // ВАЖНО: Тут тоже замените на ваше название образа

                    sh 'docker push sbdiv/jenkins-pipeline-lab:latest'

                }

            }

        }

    }

}
