pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'BUILD'
	sh 'docker build -t app-jenkins:test .'
      }
      post {
        always {
          echo 'always execute'

        }

        failure {
          echo 'it is fail'

        }

        success {
          echo 'it is success'

        }

      }
    }
    stage('Test') {
      steps {
        echo 'TEST'
        sh '/bin/nc -vz localhost 22'
        sh '/bin/nc -vz localhost 8080'
      }
    }
    stage('Push Registry') {
      steps {
        echo 'Push registry'
        sh 'docker tag app-jenkins:test app-jenkins:stable'
        sh 'docker push app-jenkins:stable'
      }
    }
  }
}
