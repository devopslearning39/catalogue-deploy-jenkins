pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }

    options {
        ansiColor('xterm')
    }

    parameters {
        string(name: 'version', defaultValue: '', description: 'What is the version ?')
    }

    stages {
        stage('Get the version') {
            steps {
                sh """
                    echo "Deploying catalogue version: ${params.version}"
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