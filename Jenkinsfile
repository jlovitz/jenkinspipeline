pipeline {
    agent any
    tools{
      maven 'localMaven'
      jdk 'localjdk'
    }

  stages{
          stage('Build'){
              steps {
                  sh 'mvn clean package'
              }
              post {
                  success {
                      echo 'Now Archiving...'
                      archiveArtifacts artifacts: '**/target/*.war'
                  }
              }
          }
          stage('Deploy to Staging'){
            steps{
              build job: 'Deploy-to-staging'
            }
          }
          stage ('Deploy to Production'){
            steps {
              timeout(time:5, unit:'DAYS'){
                input message: 'Approve PRODUCCTION Deployment?'
              }
              build job: 'Deploy-to-Prod'
            }
            post{
              success{
                echo 'code Deployment to Production'
              }
              failure{
                echo 'deployment failed.'
              }
            }
        }
      }
}
