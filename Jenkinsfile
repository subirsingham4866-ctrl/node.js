pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/subirsingham4866-ctrl/node.js.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run App Check') {
            steps {
                sh 'node -c app.js'
            }
        }

        stage('Start App with PM2') {
            steps {
                sh '''
                sudo npm install -g pm2
                pm2 delete node-app || true
                pm2 start app.js --name node-app
                pm2 save
                '''
            }
        }
    }
}
