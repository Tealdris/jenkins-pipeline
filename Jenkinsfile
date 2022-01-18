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

            stage ('Deploy-to-tomcat') {
                steps {
                    sshagent(['tomcat']) {
                        sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@192.168.122.103://opt/tomcatwebapps/webapp.war'
                    }
                     'Deploy Phase'
                }
            }
        }        
}