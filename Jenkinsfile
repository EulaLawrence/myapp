pipeline {
    agent any

    stages {
        stage('build and run') {
            steps {
                sh '''
                ls -l
                pm2 start app.js
                sleep 5
                '''
            }
        }
        stage('test the app') {
            steps {
                sh '''
                curl http://localhost:4300/api/v1/test
                '''
            }
        }
    }
}
