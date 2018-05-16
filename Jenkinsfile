pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'BUILD'
	sh 'docker build -t app .'
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
      }
    }
    stage('Deploy') {
      steps {
        echo 'DEPLOY'
      }
    }
  }
}
