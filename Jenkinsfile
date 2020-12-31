node('jenkins-slave') {

  stages {

    stage('Checkout Source') {
      steps {
        git 'https://github.com/saracm93/kube-demo.git'
      }
    }

    stage('Deploy App') {
      steps {
        script {
          kubernetesDeploy(configs: "deployment.yaml")
        }
      }
    }

  }

}

