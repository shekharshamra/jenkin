pipeline {

    agent any
    tools {
        maven 'MVN_3.6.1' 
    }
    stages {
        stage('Compile stage') {
            steps {
                sh "mvn clean install" 
        }
    }

         stage('testing stage') {
             steps {
                sh "mvn test"
        }
    }

        stage('Deploy') {
            steps {
                sh "scp -r /root/.jenkins/workspace/decl-pipeline/in28minutes-web-servlet-jsp/target/*.war root@10.17.2.171:/opt/apache-tomcat-8.5.40/webapps/"
            }
        }

  }

}
