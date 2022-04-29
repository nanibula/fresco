pipeline{
  agent any
  stages{
    stage('SCM'){
       git 'https://github.com/nanibula/fresco.git'
                }    
    stage('build'){
       sh 'mvn clean install'
       archiveArtifacts artifacts: 'target/*.war'
                  }
    stage('Deploy'){
        sshagent(['tomcat_pipeline']) {
         sh 'scp -o StrictHostKeyChecking=no target/webapp.war nani@192.168.1.108:/var/lib/tomcat9/webapps/'
                     }
                    }
}
}
