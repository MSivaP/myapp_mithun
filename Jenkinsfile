pipeline
{
    agent any
        tools
        {
            maven "maven-3.9.16"
        }
            stages
    {
        stage('GitSourceCode')
        {
            steps
            {
                git credentialsId: '74c5857f-4f7c-4a49-8281-7fcf4716b5d9', url: 'https://github.com/MSivaP/myapp_mithun.git'
            }
        }
stage('Build the package')
{
    steps
    {
        sh "mvn clean package"
    }
}
stage('Deploy the war file into the tomcat')
{
    steps
    {
        sshagent(['437a0c97-90cf-47be-930e-0448326c1ce5']) {
 sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.224.147.81:/opt/tomcat/webapps"
}
    }
}
    }
    }
