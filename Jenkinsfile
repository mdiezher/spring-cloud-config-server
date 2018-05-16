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
        sh 'docker run --rm -name app-jenkins -id -p 80:80 app-jenkins:test'
        sh '/bin/nc -vz localhost 80'
      }
    }
    stage('Push Registry') {
      steps {
        echo 'Push registry'
        sh 'docker tag app-jenkins:test mdiezher/app-jenkins:stable'
        sh 'docker push mdiezher/app-jenkins:stable'
      }
    }
  }
}
