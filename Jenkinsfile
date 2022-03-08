pipeline{
    agent any
    environment{
        VERSION = "${env.BUILD_ID}"
    }
    stages{
        stage("sonar qube analysis"){
            agent{
               docker {
                    image 'openjdk:11'
               }
            }
            steps{
               script{
                withSonarQubeEnv(credentialsId: 'sonarqube') {
                      sh '''
                      chmod +x gradlew
                      ./gradlew sonarqube 
                      '''
                    }
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

