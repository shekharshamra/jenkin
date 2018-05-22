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
       sh " if git rev-parse ${mvn_version} ;the 
               echo "Found ${mvn_version} tag"
	           exit 1
             else
                echo "create tag for ${mvn_version}"
                      git tag ${mvn_version}
                      git push origin ${mvn_version}
                      fi "
      }
      }
     
}
