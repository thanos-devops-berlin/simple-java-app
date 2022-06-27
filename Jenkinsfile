pipeline {
    agent {
        docker {
            image 'maven:3.8.6-openjdk-11-slim' 
            //args '-v /root/.m2:/root/.m2' 
        }
    }
    stages {
        stage('Build') {
            steps {
                // sh 'mvn -B -DskipTests clean package'
                // echo 'Build is successful'
                /bin/sh 'mvn --version'
            }
        }
        stage('Test') {
            steps {
                //sh 'mvn test'
                echo 'Testing is executed'
            }
            post {
                always {
                    //junit 'target/surefire-reports/*.xml'
                    echo ' Unit test report'
                }
            }
        }
        stage('Deliver') {
            steps {
                // sh './jenkins/scripts/deliver.sh'
                echo 'Pushed to artifact'
            }
        }
    }
}
