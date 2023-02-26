node{
    echo "Job name is : ${env.JOB_NAME}"
    echo "Build number is : ${env.BUILD_NUMBER}"
    
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])

def mavenhome = tool name: "maven 3.8.7"
stage('checkoutcode'){
git branch: 'development', credentialsId: 'bd32af09-bc4e-4250-aa29-7a08eb887a9c', url: 'https://github.com/KalyanReddy1508/maven-web-application.git'
}
stage('Build'){
sh "${mavenhome}/bin/mvn clean package"

}
 /* 
stage('Executesonarqube'){
sh "${mavenhome}/bin/mvn clean sonar:sonar"

}
stage('Uploadartifactintonexus'){
sh "${mavenhome}/bin/mvn clean deploy"

}

stage('Deployintotomcat'){
sshagent(['2cbc8b99-1c3a-4ce0-9d84-a4c959c7c459']) {
sh "scp -o StrictHostKeyChecking=no  target/maven-web-application.war ec2-user@172.31.24.230:/opt/apache-tomcat-9.0.71/webapps/"
}

}
*/
}
