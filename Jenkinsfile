node{

echo "The Job name is: ${JOB_NAME}"
echo "The Build number is: ${BUILD_NUMBER}"
echo "The Node name is: ${NODE_NAME}"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])

def mavenHome = tool name: 'maven3.8.8'

stage('CheckoutCode'){
git branch: 'development', credentialsId: 'd4cf479d-f673-46d2-8cc3-98baa4792812', poll: false, url: 'https://github.com/Timtobomotayo/maven-web-application.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}

/*
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}

stage('UploadArtifactsIntoNexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}

stage('DeployAppintoTomcat'){
sshagent(['6e4a5010-ccdd-4b17-9df8-b1f5e5c7dfd0']) {
  sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.5.24:/opt/apache-tomcat-9.0.73/webapps/"
}
}
*/

}
