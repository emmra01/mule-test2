pipeline {
  agent any
  stages {
    stage('Escaneo SonarQube') {
      steps {
        sh 'mvn clean verify sonar:sonar -D"sonar.projectKey=pruebas2-mulesoft" -D"sonar.host.url=http://172.17.0.2:9000" -D"sonar.login=sqp_1a1f3654184ae9a0cd3824c77cf6090f8c723e84"'
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