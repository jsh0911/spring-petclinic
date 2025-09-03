pipeline {
  agent any

  tools {
    maven "M3"
    jdk "JDK17"
  }

  stages{
    stage('Git Clone'){
      steps {
        git url: 'https://github.com/sjh4616/spring-petclinic.git', branch: 'main'
      }
    }
    stage('Maven Build'){
      steps {
        sh 'mvn -Dmaven.test.failure.ignore=true clean package'
      }
    }
    stage('Docker Image Create') {
      steps {
        sh """
        docker build -t s4616/spring-petclinic:$BUILD_NUMBER .
        docker tag s4616/spring-petclinic:$BUILD_NUMBER s4616/spring-petclinic:latest
        """
      }
    }
  }
}





