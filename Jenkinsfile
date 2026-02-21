pipeline {
    agent any

    environment {
    DOTNET_ROOT = '/opt/dotnet'
    PATH = "/opt/dotnet:${env.PATH}"
    DOTNET_SYSTEM_GLOBALIZATION_INVARIANT = 'true'
}

    triggers {
        githubPush()
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Restore') {
            steps {
                sh 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                sh 'dotnet build --no-restore'
            }
        }

        stage('Test') {
            steps {
                sh 'dotnet test --no-build --verbosity normal'
            }
        }
    }

    post {
        always {
            echo 'Pipeline complete.'
        }
    }
}