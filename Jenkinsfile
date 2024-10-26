pipeline {
    agent {
        docker {
            image 'maven:3.8.6-openjdk-11'
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
    }
}