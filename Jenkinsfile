pipeline {
  agent any
  stages {
    stage('Escaneo SonarQube') {
      steps {
        sh 'mvn clean verify sonar:sonar -D"sonar.projectKey=pruebas-mulesoft" -D"sonar.host.url=http://172.17.0.2:9000" -D"sonar.login=sqp_5dc5fc10600aa17c9e2b83dff76b1ca245dda2fb"'
      }
    }
    stage('Deploy CloudHub') {
      environment {
        ANYPOINT_CREDENTIALS = credentials('anypoint.credentials')
      }
      steps {
        sh 'mvn clean package -nsu -DskipMunitTests'
      }
    }
  }
}