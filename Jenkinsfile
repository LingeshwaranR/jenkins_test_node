node {
     def app 
     stage('clone repository') {
      checkout scm  
    }
     stage('Build docker Image'){
        sh 'env'
      app = docker.build("lingeshwaranr911/jenkins_test")
    }
     stage('Test Image'){
       app.inside {
         sh 'echo "TEST PASSED"'
      }  
    }
     stage('Push Image'){
       docker.withRegistry('https://registry.hub.docker.com', 'git') {            
       app.push("${env.BUILD_NUMBER}")            
       app.push("latest")   
   }
}
}