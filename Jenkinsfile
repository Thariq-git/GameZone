pipeline {
    agent any

    tools {
        maven 'maven 3.9.8'
        jdk 'OpenJdk11'
    }

    environment {
        SONARQUBE_URL = 'http://localhost:9000/'
        SONARQUBE_TOKEN = 'squ_32e9ca8ad20fc979b6992e37e3404ca5fc96d69c'
    }

    stages {
        stage('Clean') {
            steps {
                echo 'Start Clean'
                sh 'mvn clean'
            }
        }

        stage('Test') {
            steps {
                echo 'Start Test'
                sh 'mvn test'
            }
        }

		stage('Build') {
            steps {
                echo 'Start Build'
                sh 'mvn install -DskipTests'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                echo 'Start SonarQube Analysis'
                sh "mvn sonar:sonar -Dsonar.host.url=${env.SONARQUBE_URL} -Dsonar.login=${env.SONARQUBE_TOKEN}"
            }
        }

       
        }
    }

