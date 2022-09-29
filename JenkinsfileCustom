node{
	def mavenHome = tool name : "Maven3.8.6"
	stage('checkOutCode')
	{
	git branch: 'development', credentialsId: '932359a2-88b0-4663-89ac-49bdc4b7fc51', url: 'https://github.com/yganeshreddy/maven-web-application.git'
	}
	stage('Build')
	{
	sh "${mavenHome}/bin/mvn clean package"
	}
	stage('deployToContainer')
	{
	sshagent(['3a49221f-a468-42ca-86ce-e1949f4f89f5']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.126.207.206:/usr/local/tomcat9/webapps/"
	}
	}
}
