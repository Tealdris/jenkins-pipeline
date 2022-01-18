pipeline {
    agent {
        node {
          label 'ubuntu'
      }
  }
    tools {
        maven 'maven3'
    }

    stages {
        stage ('clean up') {
            steps {
                cleanWs()
                sh """
                echo "Cleaned Up Workspace for ${APP_NAME}"
                """
            }
        }
        stage('Code Checkout') {
            steps {
                sh """
                echo "Cleaned Up Workspace for ${APP_NAME}"
                """
            }
        }
            

    }
}