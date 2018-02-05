node('master') {
    stage ( 'git checkout' ) {
       git 'https://github.com/shekharshamra/jenkin.git' 
    }
    stage ('sonar') {
       def dockerImage = 'sonarqube:7.0-alpine'
       def host_port = '9091'
        def sonarqube_port = '9000'
        sh " docker run -d -p ${host_port}:${sonarqube_port} --name=soanrqube ${dockerImage} " 
    }
   stage ('maven') {
    def dockerImage = 'maven:slim'
     docker.image(dockerImage).inside("-v ${WORKSPACE}:/root ") {
      sh " 'mvn' -Dmaven.test.failure.ignore clean install "
   }
  }
  }
