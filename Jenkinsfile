node('master') {
    stage ( 'git checkout' ) {
       git 'https://github.com/shekharshamra/jenkin.git' 
    }
    stage ('docker') {
    def dockerImage = 'maven:slim'
     docker.image(dockerImage).inside("-v ${WORKSPACE}:/root ") {
      sh " 'mvn' -Dmaven.test.failure.ignore clean install "
   
   }
    }    
    stage ('sonar') {
    def dockerImage = 'sonarqube'
     docker.image(dockerImage).inside("-v ${WORKSPACE}:/root ") {
      sh " 'mvn' org.sonarsource.scanner.maven:sonar-maven-plugin:3.2:sonar" 
    }
    }
}
