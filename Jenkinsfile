pipeline {

  environment {
    registry = "saracm118/nginx"
    registryCredential = 'DockerHub'
    dockerImage = ""
  }

  agent {label 'jenkins-slave'}

  stages {

    stage('Checkout Source') {
      steps {
        git 'https://github.com/saracm93/kube-demo.git'
      }
    }

    stage('Build image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }

    stage('Push Image') {
      steps{
        script {
          docker.withRegistry( "" ) {
            dockerImage.push()
          }
        }
      }
    }

    stage('Cleaning up') { 
      steps {
        sh "docker rmi $registry:$BUILD_NUMBER"
      }
    }

    stage('Deploy App') {
      steps {
        script {
          kubernetesDeploy(configs: "deployment.yaml", kubeconfigId: "config")
      }
    }
  }
}
post {
    success {
      slackSend(message: "Pipeline is successfully completed.")
    }
    failure {
      slackSend(message: "Pipeline failed. Please check the logs.")
    }
}
}
