node('master') {
    stage ( git checkout ) {
        checkout scm 
    }
    stage ('docker') {
    def dockerImage = 'maven:slim'
     docker.image(dockerImage).inside {
     #   sh " 'mvn' -Dmaven.test.failure.ignore clean install "
   
   }
    }    
    }
