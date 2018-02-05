node('master') {
    stage ( 'git checkout' ) {
       git 'https://github.com/shekharshamra/jenkin.git' 
    }
    stage ('sonar') {
       def dockerImage = 'sonarqube:7.0-alpine'
       def host_port = '9091'
        def sonarqube_port = '9000'
        sh " docker run -d --name=soanrqube ${dockerImage} " 
    }
   stage ('maven') {
    def dockerImage = 'maven:slim'
     docker.image(dockerImage).inside("-v ${WORKSPACE}:/root ") {
      sh " 'mvn' -Dmaven.test.failure.ignore clean install "
      sh " 'mvn' org.sonarsource.scanner.maven:sonar-maven-plugin:3.2:sonar -Dsonar.host.url=http://172.17.0.1:9000 "
   }
  }
    stage ('clean') {
     sh " docker rm -f soanrqube "
  }
}
