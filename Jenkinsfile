pipeline {

    agent {
        node {
          label 'ubuntu'
      }
    }

    tools { 
        maven "MAVEN_HOME"
        jdk "JAVA_HOME"

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