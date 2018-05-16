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
        sh 'docker run --rm --name app-jenkins -id -p 80:80 app-jenkins:test'
        sh '/bin/nc -vz localhost 80'
      }
      post {
        always {
	  sh 'docker container stop app-jenkins'	
        }
      }
    }
    stage('Push Registry') {
      steps {
        echo 'Push registry'
        sh 'docker tag app-jenkins:test mdiezher/app-jenkins:stable'
        // This step should not normally be used in your script. Consult the inline help for details.
        withDockerRegistry([credentialsId: 'a45693dc-92da-4927-8477-2aead390a698']) {
             sh 'docker push mdiezher/app-jenkins:stable'
        }
      }
    }
  }
}
