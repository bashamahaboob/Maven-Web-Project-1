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
    if(isUinx()){
        sh 'mvn clean package'
    }
	else
	{
		bat 'mvn clean package'
	}
    
	//SonarQube
    stage('SonarQube')
    if(isUnix())
	{
        sh 'mvn sonar:sonar'
    }
	else
	{
		bat 'mvn sonar:sonar'
	}
	
    //Deploy aartifactories
    stage('To store Artifactories')
    if(isUinx())
	{
        sh 'mvn deploy'
    }
	else
	{
		bat 'mvn deploy'
	}
	
	//To Deploy Tomcat
    stage('Deployment for Servers')
    if(isUinx())
	{
        sh 'cp $WORKSPACE/**/*.war /opt/apache-tomcat-8.5.39/webapps'
    }
	else
	{
		bat 'copy %WORKSPACE%/**/*.war /opt/apache-tomcat-8.5.39/webapps'
	}
		
}
