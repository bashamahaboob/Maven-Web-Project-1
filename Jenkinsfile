#!groovy
pipeline ()
{
    //GitHub
    stage('Checkout')
    {
        git branch: 'stage', credentialsId: 'Github', url: 'https://github.com/bashamahaboob/Maven-Web-Project-1.git'
    }
    // Maven Life cycle
    stage('Maven Lifecycle')
    {
        sh 'mvn clean package'
    }
	//SonarQube
    stage('SonarQube')
    {
        sh 'mvn sonar:sonar'
    }
    //Deploy aartifactories
    stage('To store Artifactories')
    {
        sh 'mvn deploy'
    }
	//To Deploy Tomcat
    stage('Deployment for Servers')
    {
        sh 'cp $WORKSPACE/**/*.war /opt/apache-tomcat-8.5.39/webapps'
    }	
}
