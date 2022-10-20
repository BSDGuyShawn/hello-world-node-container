pipeline {
  agent {
    kubernetes {
      defaultContainer 'jnlp'
      yamlFile 'agentpod_containers.yml'
    }
  }
  
  stages {
    stage('Build-Docker-Image') {
      steps {
        container('buildah') {
          sh 'buildaj build -t slw/hello-world-node-container:latest .'
        }
      }
    }
  }
 }
  