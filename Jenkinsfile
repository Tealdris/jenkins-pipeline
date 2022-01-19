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

        stage ('Sourse-composition-analysis') {
            steps {
                sh '''
                    ip a
                    pwd
                    whoami
                    ping -c 5 8.8.8.8
                    ping -c 5 raw.githubusercontent.com
                    rm owasp* || true 
                    wget 'https://raw.githubusercontent.com/Tealdris/jenkins-pipeline/main/owasp-dependency-check.sh'
                    chmod +x owasp-dependency-check.sh
                    bash owasp-dependency-check.sh
                    cat /home/ubuntu//OWASP-Dependency-Check/reports/dependency-check-report.xml
                '''
            }
        }
        
        stage ('SAST') {
            steps {
                withSonarQubeEnv('sonar') {
                    sh '''
                        mvn -e clean package sonar:sonar
                        cat target/sonar/report-task.txt
                    '''
                }
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

            stage ('DAST') {
                steps {
                    sshagent(['zap']) {
                                 sh 'ssh -o  StrictHostKeyChecking=no ubuntu@192.168.122.93 "docker run -t owasp/zap2docker-stable zap-baseline.py -t http://192.168.122.103:8080/webapp/" || true'
                    }
                }            
        }

    }        
}