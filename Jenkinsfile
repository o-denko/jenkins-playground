pipeline {
    agent any

    environment {
        REMOTE_HOST = '172.17.0.1' 
        SSH_USER = 'osvyrydenko'
    }

    stages {
        stage('Install Apache') {
            steps {
                sshagent(['ubuntu-ssh-creds']) { // ID credentials Jenkins
                    sh "ssh -tt -o StrictHostKeyChecking=no ${SSH_USER}@${REMOTE_HOST} 'sudo apt update && sudo apt install -y apache2'"
                }
            }
        }

        stage('Check Logs for Errors') {
            steps {
                sshagent(['ubuntu-ssh-creds']) {
                    script {
                        // checking for 4xx and 5xx errors in the logs
                        def status = sh(
                            script: "ssh ${SSH_USER}@${REMOTE_HOST} 'grep -E \"HTTP/1\\..\\\" [45][0-9]{2}\" /var/log/apache2/access.log || true'",
                            returnStdout: true
                        ).trim()
                        
                        if (status) {
                            echo "Errors found in logs:\n${status}"
                        } else {
                            echo "No 4xx/5xx errors detected."
                        }
                    }
                }
            }
        }
    }

    post {
        always {
            echo "Pipeline completed."
        }
    }
}
