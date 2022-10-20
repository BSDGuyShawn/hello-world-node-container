pipeline {
  agent {
    kubernetes {
      defaultContainer 'jnlp'
      yamlFile 'agentpod_containers.yml'
    }
  }
  
  stages {
    stage('Docker-Image') {
      steps {
        container('docker') {
          sh 'docker build -t slw/hello-world-node-docker:latest .'
        }
      }
    }
    stage('Buildah-Image') {
      steps {
        container('buildah') {
          sh 'buildah --storage-driver vfs bud -t hello-world-node-buildah -f Dockerfile .'
          sh 'buildah commit'
          sh 'sleep 5'
          sh 'buildah images'
          sh 'buildah push hello-world-node-buildah docker:///slw/hello-world-node-buildah:latest'
        }
      }
    }
  }
 }
  