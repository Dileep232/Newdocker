pipeline {
  agent any
  stages {
    stage ('code checkout') {
      steps {
        git 'https://github.com/Dileep232/Newdocker.git'
      }
    }
    stage ('creating image with docker file') {
      steps {
        sh '''
        docker rmi -f myimage:one || true
        docker build -t myimage:one .'''
      }
    }
    stage ('deploying image to container') {
      steps {
        sh '''
        docker rm -f c1 || true
        docker run -d --name c1 -p 9000:80 myimage:one'''
      }
    }
  }
}
