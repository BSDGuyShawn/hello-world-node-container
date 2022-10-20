pipeline {
  agent {
    kubernetes {
      defaultContainer 'jnlp'
      yamlFile 'agentpod_containers.yml'
    }
  }
  
  stages {
    stage('Buildah-Docker-Image') {
      steps {
        container('docker') {
          sh 'docker build -t slw/hello-world-node-docker:latest .'
        }
      }
    }
    stage('Buildah-Docker-Image') {
      steps {
        container('buildah') {
          sh 'buildah bud -t slw/hello-world-node-buildah:latest .'
        }
      }
    }
  }
 }
  