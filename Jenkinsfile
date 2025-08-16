pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }

    environment {
        PackageVersion = ''
    }

    options {
        ansiColor('xterm')
    }
    stages {
        stage('Get the version') {
            steps {
                sh '''
                    echo "version: ${params.version}"
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