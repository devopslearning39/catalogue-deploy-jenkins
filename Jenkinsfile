pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }

    // environment { 
    //     packageVersion = ''
    //     nexusURL = '172.31.5.95:8081'
    // }

    options {
        ansiColor('xterm')
    }

    parameters {
        string(name: 'version', defaultValue: '', description: 'What is the artifact version?')
        string(name: 'environment', defaultValue: 'dev', description: 'What is environment?')
    }

    stages {
        stage('Print version') {
            steps {
                sh """
                    echo "version: ${params.version}"
                    echo "environment: ${params.environment}"
                """
            }
        }
    }

    post {
            always {
                echo 'This will invoke all the time of jenkins execution..'
                deleteDir()     //This used to delete the zip file in node agent once the artifact uploaded to into Nexus repo (To reduce the memory in node)
            }
            failure {
                echo 'Jella, build got failed, Please check!'
            }
            success {
                echo 'Booom!!!, Jella build executed successfully.'
            }
    }
}