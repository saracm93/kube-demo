pipeline {
    agent { label 'jenkins-slave' } 
    stages {
        stage('Checkout') {
          steps {
            git url:'https://github.com/saracm93/kube-demo.git'
          }
        }
        stage('deploy') {
          steps {
            kubernetes {
              yamlFile 'deployment.yaml'
            }
          }
        }
    }
}