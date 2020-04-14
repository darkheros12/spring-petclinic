pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building project...'
      }
    }

    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            echo 'Test'
          }
        }

        stage('Error') {
          steps {
            warnError(message: 'An Error as occurred')
          }
        }

      }
    }

    stage('Package') {
      steps {
        echo 'Package'
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploy'
      }
    }

  }
  post {
    always {
      emailext(body: 'A Test EMail', recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']], subject: 'Test')
    }

  }
}