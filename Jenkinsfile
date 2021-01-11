pipeline {
    agent { label 'jenkins-slave' } {
        stage('Checkout') {
          steps {
            git url:'https://github.com/saracm93/kube-demo.git'
          }
        }
        kubernetes {
          yamlFile 'deployment.yaml'
        }
    }
}