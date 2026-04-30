pipeline
{
    agent any
    stages
    {
        stage('ContDownload')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/maven.git'
            }
        }
        stage('ContBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContDeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '4c5d7f09-7e52-4578-90f7-28debcf39930', path: '', url: 'http://172.31.16.120:8080')], contextPath: 'test1', war: '**/*.war'
            }
        }
        stage('ContTesting')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
            
        }
        stage('ContDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '4c5d7f09-7e52-4578-90f7-28debcf39930', path: '', url: 'http://172.31.23.123:8080')], contextPath: 'prod1', war: '**/*.war'
            }
        }
    }
}
