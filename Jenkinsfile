pipeline {
  agent any
    stages {
        stage ('Build') {
            steps {
                sh '''#!/bin/bash
                python3.7 -m venv venv
                source venv/bin/activate
                pip install pip --upgrade
                pip install -r requirements.txt
                '''
            }
        }
        stage ('Test') {
            steps {
                sh '''#!/bin/bash
                #source venv/bin/activate
                #py.test --verbose --junit-xml test-reports/results.xml
                echo "This is a test stage"
                '''
            }
            post {
                always {
                    junit 'test-reports/results.xml'
                }
            }
        }
    stage ('Deploy') {
            steps {
                sh '''#!/bin/bash
                source venv/bin/activate
                eb create workload2-2 --single
                '''
            }
        }
    }
}
