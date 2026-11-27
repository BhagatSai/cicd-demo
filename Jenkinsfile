pipeline {
  agent any
  environment {
    IMAGE = "BhagatSai/myapp"
  }
  stages {
    stage('Maven Build') {
      steps { sh 'mvn clean package -DskipTests' }
    }
    stage('Docker Build') {
      steps { sh 'docker build -t $IMAGE:$BUILD_NUMBER .' }
    }
    stage('Docker Push') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'U', passwordVariable: 'P')]) {
          sh '''
            echo $P | docker login -u $U --password-stdin
            docker push $IMAGE:$BUILD_NUMBER
          '''
        }
      }
    }
  }
}
