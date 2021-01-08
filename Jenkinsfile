pipeline {
    agent { label 'jenkins-slave' }

    stages {
      stage('Checkout Source') {
        steps {
          git 'https://github.com/saracm93/kube-demo.git'
        }
      }
      stage('Build docker image') {
        steps {
          sh "sudo docker build . -t nginx:1"
        }
      }
      stage('Push Image to OCIR'){
        steps {
          sh "sudo docker login -u 'kubernetes' -p 'r9A:K<61Hv)2D5]X5AW+' syd.ocir.io"
          sh "sudo docker tag nginx:1 syd.ocir.io/sdeeaoej8ii1/nginx:1"
          sh 'sudo docker push syd.ocir.io/sdeeaoej8ii1/nginx:1'
        }
      }
    }