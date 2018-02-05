node('master') {
    stage ( 'git checkout' ) {
       git 'https://github.com/shekharshamra/jenkin.git' 
    }
    
     stage ('maven') {
     def dockerImage = 'maven:slim'
      docker.image(dockerImage).inside("-v ${WORKSPACE}:/root ") {
      sh " 'mvn' -Dmaven.test.failure.ignore clean install "
      sh " 'mvn' org.sonarsource.scanner.maven:sonar-maven-plugin:3.2:sonar -Dsonar.host.url=http://172.17.0.1:9000 "
   }
  }
}
