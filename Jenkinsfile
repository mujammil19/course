pipeline {
  agent any
  stages{
    stage('Build'){
      steps {
              sh 'mvn clean package'
      }
        post {
          success { 
              echo 'Now Archiving...'
              archiveArtifacts artifacts: '**/target/*.war'
          }
        }
     }
    
    stage ('Deployments'){
      parallel{
        stage ('Deploy to Staging'){
          steps {
                sh "cp **/target/*.war /usr/local/apache-tomcat9/webapps"
          }
        }
      }
      post {
        success {
          mail to: 'manikyammujammil@gmail.com', subject: 'job is success', body: 'this is test'
        }
      }
    }
  }
}
