pipeline
{
    agent any
    stages
    {
        stage(ContinuousDownload)
        {
            steps
            {
                git 'https://github.com/Sriranganath007/maven.git'
            }
        }
        stage(ContinuousBuild)
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage(ContinuousDeploy)
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'b478a794-4799-41fc-873c-07a7142fa340', path: '', url: 'http://172.31.20.18:8080')], contextPath: 'testapp', war: '**/*.war'
            }
        }
        stage(ContinuousTesting)
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /home/ubuntu/.jenkins/workspace/Sample-1-Declar/testing.jar'
            }
        }
        stage(ContinuousDelivery)
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'b478a794-4799-41fc-873c-07a7142fa340', path: '', url: 'http://172.31.26.100:8080')], contextPath: 'prodapp', war: '**/*.war'
            }
        }
    }
}
