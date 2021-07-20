pipeline {
  agent any
  tools {
     maven 'M2_HOME'
  }
  environment {
    registry = "3908vision/160k"
    registryCredential = '827c7fa5-e067-4a9e-92f4-c5590cbf7eee'
  }
  stages {
    stage('Build'){
      steps {
       sh 'mvn clean'
       sh 'mvn install'
       sh 'mvn package'
      }
    }
    stage('test'){
      steps {
       echo "test step"
       sh 'mvn test'
      }
    }
    stage('Deploy'){
      steps {
       script {
        docker.build registry + ":$BUILD_NUMBER"
       }
       }
      }
 }
}
