pipeline{
  agent any
  stages{
    stage('Build'){
      steps{
        sh 'mvn clean package-pipeline'
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
