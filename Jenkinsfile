pipeline {
    agent {label 'devops-01-ulil'}

    stages {
        stage('Pull Source Code') {
            steps {
                git branch: 'main', url: 'https://github.com/omahkoding/laravel-blog.git'
            }
        }
        stage('Testing Application') {
            steps {
                echo 'Testinf Application'
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
