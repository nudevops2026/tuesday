pipeline
{
    agent any
    stages
        {
            stage('Download')
            {
                steps
                {
                  git 'https://github.com/IntelliqDevops/maven.git'
                } 
            }
            stage('Build')
            {
                steps
                {
                  sh 'mvn package'
                } 
            }
            stage('Deploy')
            {
                steps
                {
                  deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '32290ecb-2fc6-45a7-a901-3e7a7624e83c', path: '', url: 'http://98.70.41.92:8080/')], contextPath: 'mytestapp', war: '**/*.war'
                } 
            }
             stage('Testing')
            {
                steps
                {
                 git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                 sh 'java -jar /var/lib/jenkins/workspace/declarativepipeline/testing.jar'
                 
                } 
            }
            stage('Delivery')
            {
                steps
                {
                  deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '32290ecb-2fc6-45a7-a901-3e7a7624e83c', path: '', url: 'http://57.159.24.46:8080/')], contextPath: 'myprodapp', war: '**/*.war'
                } 
            }
          
        }
}
