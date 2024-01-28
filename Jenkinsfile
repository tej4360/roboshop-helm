pipeline {

  agent any

  parameters {
    string(name: 'component', defaultValue: '', description: 'App Component Name')
  }

  stages {

    stage('Clone App Repo') {
      steps {
        dir('APP') {
          git branch: 'main', url: 'https://github.com/tej4360/${component}.git'
        }
        dir('HELM') {
          git branch: 'main', url: 'https://github.com/tej4360/roboshop-helm.git'
        }
      }

    }

    stage('Helm Deploy') {
      steps {
        dir('HELM') {
          sh 'helm upgrade -i ${component} . --kubeconfig=/etc/rancher/k3s/k3s.yaml -f ../APP/values.yaml'
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