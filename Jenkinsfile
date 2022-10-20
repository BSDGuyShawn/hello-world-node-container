pipeline {
  agent {
    kubernetes {
      defaultContainer 'jnlp'
      yamlFile 'agentpod_containers.yml'
    }
  }
  
  stages {
    // stage('Docker-Image') {
    //   steps {
    //     container('docker') {
    //       sh 'docker build -t slw/hello-world-node-docker:latest .'
    //     }
    //   }
    // }
    stage('Buildah-Image') {
      steps {
        container('podman') {
          // sh 'podman --storage-driver vfs build -t hello-world-node-buildah -f Dockerfile .'
          sh 'podman --url=unix://var/run/docker.sock --storage-driver vfs build -t hello-world-node-buildah:latest -f Dockerfile . --format=docker'
          sh 'sleep 5'
          sh 'podman images'
          sh 'podman push hello-world-node-buildah docker://hello-world-node-buildah'
        }
      }
    }
  }
 }
  