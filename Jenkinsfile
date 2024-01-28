pipeline {

  agent any

  environment {
      GIT_USERNAME = 'tej4360'
      GIT_TOKEN_CREDENTIALS = credentials('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')
      GIT_REPO_URL = 'https://github.com/tej4360/roboshop-helm.git'
  }

  parameters {
    string(name: 'component', defaultValue: '', description: 'App Component Name')
    string(name: 'version', defaultValue: '', description: 'container version')
  }

  stages {

    stage('Clone App Repo') {
      steps {
        dir('HELM') {
          git branch: 'main', url: 'https://github.com/teja4360/roboshop-helm'
        }
      }

    }

    stage('Helm Deploy') {
      steps {
        dir('HELM') {
          sh 'helm upgrade -i ${component} . -f ../APP/values.yaml --set'
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