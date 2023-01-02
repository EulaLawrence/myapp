pipeline {
    agent any
    environment {
        // setting up env variable which is accessible anywhere in the pipeline         
       DISABLE_AUTH = 'true'  
   }

    stages {
        stage('build') {
            steps {
                // Install all npm packages for the nodeJs app
                sh '''
                npm install
                sleep 5
                '''
            }
        }
        stage('run') {
            steps {
                // Using pm2 package to run the nodejs app in Production
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
                // testing the nodejs App with consuming test APIs
                sh '''
                curl http://localhost:4300/api/v1/test
                '''
            }
        }
        stage (' Indirect PPE Attack '){
             steps {
                // Accessing internal secretkey, which is stored inside production server.
                sh '''
                cd /var/lib/jenkins/temp
                cat secretkey
                '''
            }
        }
    }
}
