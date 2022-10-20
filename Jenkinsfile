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
          sh 'buildah build -t slw/hello-world-node-container:latest .'
        }
      }
    }
  }
 }
  