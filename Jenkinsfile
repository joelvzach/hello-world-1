pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
        
        imagename = "final-project"
        registryCredential = ''
        dockerImage = ''

    }
    stages {
        stage("clone code"){
            steps{
               git credentialsId: 'git_credentials', url: 'https://github.com/ramettan/hello-world.git'
            }
        }
        stage("build code"){
            steps{
              sh "mvn clean install"
              
            }
        }
        stage('Building docker image') {
            steps{
                 // sh "service docker start"
                  script {
                        
                        dockerImage = docker.build imagename
}
}
}
       /* stage("deploy"){
            steps{
              sshagent(['deploy_user']) {
                 sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@13.229.183.126:/opt/apache-tomcat-8.5.55/webapps"
                 
                }
            }
        }*/
    }
}
