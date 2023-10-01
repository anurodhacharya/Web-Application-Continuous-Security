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
          sh 'ssh -v -o StrictHostKeyChecking=no -l node2 192.168.81.135 uname -a'
           }      
        }       
    }
  }
}
