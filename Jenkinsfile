pipeline {
    agent {label 'devops-01-ulil'}

    stages {
        stage('Pull Source Code') {
            steps {
                git branch: 'main', url: 'https://github.com/omahkoding/laravel-blog.git'
            }
        }
        stage('Copy env Variable') {
            steps {
                sh '''
                cp /usr/share/nginx/html/laravel-blog/.env .env
                '''
            }
        }
        stage('Testing Application') {
            steps {
                sh '''
                composer install --dev --optimize-autoloader
                composer require fakerphp/faker --dev
                php artisan test
                '''
            }
        }
        stage('Build Container Image') {
            steps {
                echo 'Build Container Image'
            }
        }
        stage('Deploy Container Application') {
            steps {
                echo 'Deploy Container Application'
            }
        }
        stage('Publish Container Image') {
            steps {
                echo 'Publish Container Image'
            }
        }
    }
}
