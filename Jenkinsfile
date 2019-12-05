pipeline{
  agent any
  stages{
    stage('Build'){
      steps{
        sh 'mvn clean packages-pipeline'
      }
      post{
        success{
          echo 'now Archiving...'
          archiveArtifacts artifacts: '**/target/*.war'
        }
      }
    }
  }
}
