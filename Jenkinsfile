node {
    def app
    stage('Clone Git Repository') {
      checkout scm
    }

    stage('Build Docker image') {
       app = docker.build("sskrishna/achistarwebsite")
    }


    stage('Push Docker image') {
         docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
            } 
    }
    
    stag('Run/Deploy Docker Container '){
    sh 'docker run -d -p 80:80 .  
    }
    
}
