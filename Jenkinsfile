pipeline{
  agent any
  stages{
    stage('SCM-stage'){
       steps{
       git 'https://github.com/nanibula/fresco.git'
             }
                 }    
    stage('Build-stage'){
          steps{
       sh 'mvn clean install'
       archiveArtifacts artifacts: 'target/*.war'
                }
                    }
    stage('Deploy-stage'){
          steps{
        sshagent(['tomcat_pipeline']) {
         sh 'scp -o StrictHostKeyChecking=no target/webapp.war nani@192.168.1.108:/var/lib/tomcat9/webapps/'
                     }
                  }
                    }
}
}
