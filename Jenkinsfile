pipeline{
    agent any
    stages{
        stage('Code checkout'){
            steps{
                // Get the code checkout to jenkins workspace
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/thanos-devops-berlin/simple-java-app.git']]])
            }
        }
        stage('Build maven'){
            steps{
                script{
                    withMaven(maven: 'Maven3') {
                     sh 'java --version'        
                     sh 'mvn --version'
                     sh 'mvn clean compile install'
                }
                    
                }
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t manee2k6/java-app:1.0 .'
                }
            }
        }
        stage('Push docker images'){
            steps{
                withCredentials([string(credentialsId: 'github-id', variable: 'docker-pwd')]) {
                 sh 'docker login -u manee2k6 -p ${docker-pwd}'
                 sh 'docker push manee2k6/java-app:1.0 '
             }
            }
        }
    }
}
