pipeline {

  agent any

  parameters {
    string(name: 'component', defaultValue: '', description: 'App Component Name')
    string(name: 'version', defaultValue: '', description: 'container version')
  }

  stages {

    stage('Clone App Repo') {
      steps {
        dir('APP') {
          git branch: 'main', url: 'https://github.com/raghudevopsb72/${component}'
        }
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