pipeline {
    agent {
        node {
            label 'crawlab'
        }
    }

    stages {
        stage('Setup') {
            steps {
                "Running Setup..."
                sh 'source /home/yeqing/.profile'
            }
        }
        stage('Build Frontend') {
            steps {
                echo "Building frontend..."
                sh "cd frontend"
                sh "yarn install"
                sh "npm run build:prod"
                sh "#/home/yeqing/.nvm/versions/node/v8.12.0/bin/node /home/yeqing/.nvm/versions/node/v8.12.0/bin/npm install"
                sh "#/home/yeqing/.nvm/versions/node/v8.12.0/bin/node /home/yeqing/.nvm/versions/node/v8.12.0/bin/npm run build:prod"
            }
        }
        stage('Build Backend') {
            steps {
                echo "Building backend..."
                sh "cd ../crawlab"
                sh "pyenv activate crawlab"
                sh "pip install -r requirements.txt"
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}