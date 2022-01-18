pipeline {

    agent {
        node {
          label 'ubuntu'
      }
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
    
            stage ('Build Phase') {
                steps {
                    echo 'Build Phase'
                }
            }
            stage ('Test Phase') {
                steps {
                    echo 'Test Phase'
                }
            }
            stage ('Deploy Phase') {
                steps {
                    echo 'Deploy Phase'
                }
            }
        }        
}