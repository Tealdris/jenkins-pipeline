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
                    ''' 
            }
        }

        stage ('Git-Secrits') {
            steps {
                sh '''
                    rm trufflehog || true
                    docker run gesellix/trufflehog --json https://github.com/cehkunal/webapp.git > trufflehog
                    cat trufflehog
                '''
            }
        }

            stage ('Build Phase') {
                steps {
                    echo 'Build Phase'
                    sh '''
                        mvn clean package
                    '''
                }
            }

            stage ('Deploy-to-tomcat') {
                steps {
                    sshagent(['tomcat']) {
                        sh 'scp -o StrictHostKeyChecking=no /home/ubuntu/jenkins/workspace/Pipeline-job-1/target/*.war ubuntu@192.168.122.103:/opt/tomcat/webapps/webapp.war'
                    }
                }
            }
        }        
}