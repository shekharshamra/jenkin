node('master') {
    stage ( 'git checkout' ) {
       git 'https://github.com/shekharshamra/jenkin.git' 
    }
    
     stage ('maven') {
     def dockerImage = 'maven:slim'
      docker.image(dockerImage).inside("-v ${WORKSPACE}:/root ") {
      sh " 'mvn' -Dmaven.test.failure.ignore clean install "
      }
  } 
      stage (' junit'){
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
      stage('SonarQube analysis') {
       def mvnHome
        mvnHome = tool 'mvn'
      withSonarQubeEnv('sonarqube') {
      // requires SonarQube Scanner for Maven 3.2+
       sh "'${mvnHome}/bin/mvn' org.sonarsource.scanner.maven:sonar-maven-plugin:3.2:sonar"
      }
      }
}
