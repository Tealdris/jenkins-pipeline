pipeline {

    agent any

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
                        sh 'scp -v -o StrictHostKeyChecking=no /usr/share/jenkins/*.war ubuntu@192.168.122.103:/opt/tomcat/webapps/webapp.war'
                    }
                }
            }
        }        
}