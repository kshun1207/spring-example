 pipeline { 
  agent any 
  triggers { 
    pollSCM('* * * * *') 
  } 
  stages { 
    stage('Checkout') { 
      steps { 
        git branch: 'main',  
        url: 'https://github.com/kshun1207/spring-example.git' 
      } 
    } 
    stage('Build') { 
      steps { 
        sh 'mvn clean package' 
      } 
    } 
    /*stage('Test') { 
      steps { 
        sh ' ' 
      } 
    } */
    stage('Deploy') { 
      steps { 
        deploy adapters: [tomcat9(credentialsId: 'admin', url: 'http://192.168.56.102:8080')], 
        contextPath: null,
        war: 'target/hello-world.war' 
      } 
    } 
  } 
}