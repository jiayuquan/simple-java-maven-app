pipeline {
    agent {
        docker {
            image 'maven:3.9.9-eclipse-temurin-17'
            args '-v /Users/jyq/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -v'
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
             steps {
                 sh 'mvn test'
             }
             post {
                 always {
                     junit 'target/surefire-reports/*.xml'
                 }
             }
        }
        stage('Deliver') {
                 steps {
                     sh './jenkins/scripts/deliver.sh'
                 }
             }
    }
}