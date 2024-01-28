pipeline {

  agent any

  parameters {
    string(name: 'component', defaultValue: '', description: 'App Component Name')
    string(name: 'version', defaultValue: '', description: 'container version')
  }

  stages {

    stage('Clone App Repo') {
      steps {
        dir('HELM') {
          git branch: 'main', url: 'https://github.com/tej4360/roboshop-helm.git'
        }
      }

    }

    stage('Helm Deploy') {
      steps {
        dir('HELM') {
          sh '/usr/local/bin/helm upgrade -i frontend .'
        }

      }
    }

  }

  post {
      success {
          echo 'Deployment successful'
       }

      failure {
          echo 'Deployment failed'
      }
  }

}