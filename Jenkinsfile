pipeline {
    agent {label 'devops-01-ulil'}

    stages {
        stage('Pull Source Code') {
            steps {
                git branch: 'main', url: 'https://github.com/omahkoding/laravel-blog.git'
            }
        }
        //cp /usr/share/nginx/html/laravel-blog/.env .env => copy file .env dari laravel blog  ke folder /opt/jenkins/
        stage('Copy env Variable') {
            steps {
                sh '''
                cp /usr/share/nginx/html/laravel-blog/.env .env
                '''
            }
        }

        stage('Code Quality Analysis') {
            steps {
                sh '''
                  sonar-scanner \
                    -Dsonar.projectKey=laravel-blog \
                    -Dsonar.sources=. \
                    -Dsonar.host.url=http://172.23.5.2:9000 \ 
                    -Dsonar.token=sqp_9f1c597f56797fad04a1173b18033b731f40478a
                '''
            }
        }

        stage('Build Container Image') {
            steps {
                sh '''
                docker compose build
                '''
            }
        }
        stage('Deploy Container Application') {
            steps {
                sh '''
                docker compose up -d
                '''
            }
        }
        stage('Publish Container Image') {
            steps {
                 sh '''
                docker compose push
                '''
            }
        }
    }
}
