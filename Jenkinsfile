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
            }
        }
    
            stage ('Build Phase') {
                steps {
                    echo 'Build Phase'
                    sh 'mvn clean package'
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