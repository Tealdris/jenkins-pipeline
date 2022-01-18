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
                            ip a
                            whoami

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
                        sh '''
                            whoami
                            ip a
                        '''
                        sh 'ssh -v ubuntu@192.168.122.103'
                    }
                }
            }
        }        
}