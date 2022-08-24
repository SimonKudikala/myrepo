node('built-in') 
{
    stage('ContinuousDownload') 
    {
        git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('ContinuousBuild') 
    {
        sh 'mvn package'
    }
    stage('ContinuousDeploy') 
    {
        deploy adapters: [tomcat9(credentialsId: 'b2104fca-1fe9-4e7e-9bcf-d57370412baf', path: '', url: 'http://172.31.12.130:8080')], contextPath: 'mytapp', war: '**/*.war'
    }
    stage('ContinuousTesting') 
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/Scriptedpipeline02/testing.jar'
    }
    stage('ContinuousDelivery') 
    {
        deploy adapters: [tomcat9(credentialsId: 'b2104fca-1fe9-4e7e-9bcf-d57370412baf', path: '', url: 'http://172.31.11.122:8080')], contextPath: 'mypapp', war: '**/*.war'
    }
}
