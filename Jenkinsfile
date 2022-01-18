pipeline {

    agent {
        node {
          label 'ubuntu'
      }
    }

    tools { 
        maven "M3"
    }

        stages {
            stage ('clean up') {
            steps {
                cleanWs()

            }
        }
    
            stage ('something Phase') {
                steps {
                    echo 'Build Phase'
                    checkout scm
                    sh 'mvn clean package'
                }
            }
            stage ('Deploy Phase') {
                steps {
                    echo 'Deploy Phase'
                }
            }
        }        
}