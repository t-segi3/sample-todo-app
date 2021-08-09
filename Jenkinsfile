pipeline {
  agent any

    stages {
        stage('Build') {
            git url: 'https://github.com/rendyananta/sample-todo-app.git'

            def app = docker.build("rendyananta/sample-todo-app:fpm", "-f opt/container/php-fpm/Dockerfile")

            def nginx = docker.build("rendyananta/sample-todo-app:nginx", "-f opt/container/nginx/Dockerfile")
        }
        stage('Test') {
            app.inside {
                sh 'php artisan test'
            }
        }
    }
}   