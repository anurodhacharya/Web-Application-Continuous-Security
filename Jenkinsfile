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
    
    stage ('Check-Git-Secrets') {
      steps {
        sh 'rm trufflehog || true'
        sh 'docker run gesellix/trufflehog --json https://github.com/cehkunal/webapp.git > trufflehog'
        sh 'cat trufflehog'
      }
    }
    
    stage ('Build') {
      steps {
       sh 'mvn clean package'
      }
    }
    
//     stage ('Deploy-To-Tomcat') {
//       steps {
//         sshagent(['tomcat']) {
//           sh 'scp -o StrictHostKeyChecking=no target/*.war anurodh@192.168.1.163:/prod/apache-tomcat-8.5.75/webapps/webapp.war'
//            }      
//         }       
//     }
    
    
    
  }
}
