pipeline {
	agent none 

	stages {
		stage ('Checkout code') {
			agent any 
			steps {
				deleteDir()
				checkout scm
			}
		}
		stage ('Install dependencies') {
			
			steps {
				sh '''
					python --version
					pip install  -r requirements.txt
				'''
			}
		}

		stage ('Run tests') {
			
			steps {
				sh '''
					pytest
				'''
			}
		}
		stage ('Package app') {
			
			steps {
				sh '''
					mkdir -p dist
					tar -czf dist/python-app.tar.gz .
				'''
			}
		}
	}

	post {
		success {
			echo 'Pipeline completed successfully'
		}
		failure {
			echo 'Pipeline failed'
		}

	}
}