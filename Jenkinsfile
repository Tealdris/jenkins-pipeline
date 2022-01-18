pipeline {

    agent {
        node {
          label 'ubuntu'
      }
    }

    tools { 
        maven 'Apache Maven 3.6.3' 
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
            stage ('Deploy Phase') {
                steps {
                    echo 'Deploy Phase'
                }
            }
        }        
}