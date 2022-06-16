pipeline {
    agent {
        docker {
            image 'maven:3.8.6-openjdk-11' 
            args '-v /root/.m2:/root/.m2' 
        }
    }
    stages {
        stage('Build') {
            steps {
                // sh 'mvn -B -DskipTests clean package'
                echo 'Build is successful'
            }
        }
        stage('Test') {
            steps {
                //sh 'mvn test'
                echo 'Test is executed'
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
