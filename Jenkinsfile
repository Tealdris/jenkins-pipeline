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

        stage ('Sourse-composition-analysis') {
            steps {
                sh '''

                    wget 'https://raw.githubusercontent.com/Tealdris/jenkins-pipeline/main/owasp-dependency-check.sh'
                    chmod +x owasp-dependency-check.sh
                    bash owasp-dependency-check.sh
                    cat /home/ubuntu//OWASP-Dependency-Check/reports/dependency-check-report.xml
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