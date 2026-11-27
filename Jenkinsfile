pipeline {
  agent any
  stages {
    stage('Maven Build') {
      steps { sh 'mvn clean package -DskipTests' }
    }
    stage('Docker Build') {
      steps { sh 'docker build -t BhagatSai/myapp:latest .' }
    }
  }
}
