pipeline {
  agent any
  environment {
    IMAGE_NAME = "myapp"
    IMAGE_TAG = "latest"
  }
  
  stages {
    stage ('Checkout Code') {
      steps {
        git branch: 'main', url: 'https://github.com/devops-basics-project/devops-project'
      }
    }
    stage ("Build Docker Image"){
      steps {
        sh 'docker build -t $IMAGE_NAME:$IMAGE_TAG .'
      }
    }
    stage ("Run Container"){
      steps {
        sh '''
        docker stop myapp || true
        docker rm myapp || true
        docker run -d --name myapp -p 8060:80 $IMAGE_NAME:$IMAGE_TAG
        '''
      }
    }

    }
}
