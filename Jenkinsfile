pipeline {
  agent {
    label 'static-ec2'
}
  stages {
    stage('Build') {
      steps {
        echo 'Building...'
      }
    }
    stage('Test') {
      steps {
        echo 'Testing Testing...'
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying..'
      }
    }
  }
  post {
        always {
            // This will always send a message to the Slack channel
            slackSend (color: '#FFFF00', message: "Build ${currentBuild.fullDisplayName} finished with result: ${currentBuild.result}")
        }
        failure {
            // This will only send a message if the build fails
            slackSend (color: '#FF0000', message: "Build ${currentBuild.fullDisplayName} failed!")
        }
        success {
            // This will only send a message if the build is successful
            slackSend (color: '#00FF00', message: "Build ${currentBuild.fullDisplayName} succeeded!")
        }
  
     }
}