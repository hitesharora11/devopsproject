pipeline{
    agent any
    stages{
        stage("sonar quality check"){
            steps{
                agent {
                    { docker 'openjdk:11' }
                    }
                 script {
                    withSonarQubeEnv(credentialsId: 'sonarqube') {
                        sh 'chmod +x gradlew'
                        sh './gradlew sonarqube'
                        }
                    }
            }
            
        }
    }
    post{
        always{
            echo "Success"
        }
    }
}