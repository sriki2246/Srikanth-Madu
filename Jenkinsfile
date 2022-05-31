pipeline {
    agent any

    stages {
        stage('Clone SCM') {
            steps {
                echo 'Clone Repository'
               git 'https://github.com/wakaleo/game-of-life.git'
            }
        }

    stage('Build Artifact') {
            steps {
                echo 'Building war file'
            sh 'mvn clean install'
            }
        }
    stage('Deploy to Artifact') {
            steps {
                echo 'Deploying Application to Tomcat'
            deploy adapters: [tomcat9(credentialsId: '9000d1ac-c36c-470a-8b23-e1a4dde7c6ed', path: '', url: 'http://18.206.165.112:8080/')], contextPath: 'gameoflifewebapplication', war: '**/*.war'
            }
        }
    }
}
