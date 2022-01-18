pipeline {

    agent {
        node {
          label 'ubuntu'
      }
    }

    tools { 
        maven 'Maven' 
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