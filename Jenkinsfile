node(){
    def mavenHome = tool name : "Maven3.8.6"
    stage('checkoutCode'){
        git branch: 'Development', credentialsId: '97677bbc-809c-425d-abf7-1ea14498d1b2', url: 'https://github.com/yganeshreddy/maven-web-application.git'
    }
    stage('build'){
        sh "${mavenHome}/bin/mvn clean package"
    }
    stage('deployToContainer'){
        sh "cp target/maven-web-application.war /opt/tomcat8/webapps/"
    }
    stage("sendEmailNotification"){
        emailext body: '''Hi,

Build has been completed. Please check and validate.

Regards,
Jenkins.''', subject: 'Build Over!!!', to: 'Darlingprabhas1001@gmail.com'
    }
}
