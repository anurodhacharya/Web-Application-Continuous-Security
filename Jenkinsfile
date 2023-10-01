pipeline {
  agent any 
  tools {
    maven 'Maven'
  }
  stages {
    stage ('Initialize') {
      steps {
        sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
            ''' 
      }
    }
    
    stage ('Build') {
      steps {
      sh 'mvn clean package'
       }
    }

    stage ('Deploy-To-Tomcat') {
      steps {
        sshagent(['node2']) {
          sh 'scp -i /home/jenkins/id_rsa target/*.war node2@192.168.81.135:/opt/tomcat/apache-tomcat-10.1.13/webapps/webapp.war'
           }      
        }       
    }
  }
}
