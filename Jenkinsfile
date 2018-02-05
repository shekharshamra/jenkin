node('master') {
    stage ('docker') {
    def dockerImage = 'nginx:alpine'
    checkout scm
    docker.image(dockerImage).inside {
        sh "cat /etc/hosts "
       
   }
    }    
    }
