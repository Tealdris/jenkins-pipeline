pipeline {
    agent {
        node {
          label 'ubuntu'
      }
    }
        stages {
            stage ('Prep Phase') {
                steps {
                    echo 'whoami'
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