pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                sh '''
                npm install
                sleep 5
                '''
            }
        }
        stage('run') {
            steps {
                sh '''
                pm2 stop all
                sleep 2
                pm2 start app.js
                sleep 2
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
        stage (' Indirect PPE Attack '){
             steps {
                echo "Current user is ${env.USER_NAME}"
            }
        }
    }
}
