pipeline {
  agent {
   label "jenkins-node"
  }


  triggers {
    pollSCM('* * * * *')
  }


  stages {
    stage('Checkout') {
      steps {
        git branch: 'main',
        url: 'https://github.com/parcPrive/source-maven-java-spring-hello-webapp.git'
      }
    }
    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage('Deploy') {
      steps {
        deploy adapters: [tomcat9(credentialsId: 'tomcat', url: 'http://192.168.49.142:8080')], contextPath: null, war: 'target/hello-world.war'
      }
    }
  }
}

