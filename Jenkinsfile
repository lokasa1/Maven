pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContinuousDeployment')
        {
            steps
            {
               deploy adapters: [tomcat9(credentialsId: '1dd0c113-a036-45d4-9d24-8f6af7bf267c', path: '', url: 'http://172.31.10.25:8080')], contextPath: 'testapp', war: '**/*.war'
            }
        }
        stage('ContinuousTesting')
        {
            steps
            {
               git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
               sh 'java -jar /home/ubuntu/.jenkins/workspace/Scriptedpipeline/testing.jar'
            }
        }
        stage('ContinuousDelivery')
        {
            steps
            {
               deploy adapters: [tomcat9(credentialsId: '1dd0c113-a036-45d4-9d24-8f6af7bf267c', path: '', url: 'http://172.31.12.210:8080')], contextPath: 'prodapp', war: '**/*.war'
            }
        }
       
    }
    
    
    
    
    
    
    
    
}
