pipeline {
    agent any

    stages {
        stage('Run Python App') {
            steps {
                git url: 'https://github.com/OxSuyash/python-basic-app.git', branch: 'main'
                sh 'python3 app.py'  
            }
        }
    }

    post {
        success { echo 'Pipeline succeeded!' }
        failure { echo 'Pipeline failed!' }
    }
}
