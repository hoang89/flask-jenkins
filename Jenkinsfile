/* groovylint-disable-next-line CompileStatic */
pipeline {
    agent {
        docker { image 'python:3.8.0' }
    }
    stages {
        stage('build') {
            steps {
                sh 'python -m venv .pydev'
                sh 'source .pydev/bin/activate'
                sh 'pip3 install --user -r requirements.txt'
            }
        }
        stage('test') {
            steps {
                sh 'python test.py'
            }
            post {
                always {
                    junit 'test-reports/*.xml'
                }
            }
        }
    }
}
