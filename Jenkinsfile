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
        stage ('Initialize') {
            steps {
                sh '''
                            echo "PATH = ${PATH}"
                            echo "M2_HOME = ${M2_HOME}"
                    ''' 
            }
        }
    
            stage ('Build Phase') {
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