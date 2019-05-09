pipeline
{
    agent any
    stages
    {
        stage('Compile Stage')
        {
            steps
            {
                withMaven(maven : 'MAVEN_PIPELINE')
                {
                    sh 'mvn clean compile'
                }
            }
        }
        stage('Testing Stage')
        {
            steps
            {
                withMaven(maven : 'MAVEN_PIPELINE')
                {
                    sh 'mvn test'
                }
            }
        }
        
    }
}
