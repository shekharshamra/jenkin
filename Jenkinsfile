node('master') {
    stage ('docker') {
    def dockerImage = 'maven:slim'
    checkout scm
    docker.image(dockerImage).inside {
        sh " 'mvn' -Dmaven.test.failure.ignore clean install "
   
   }
    }    
    }
