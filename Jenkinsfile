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
			agent {
				docker {
					image 'python:3.10-slim'
				}
			}
			steps {
				sh '''
					python --version
					pip install --user -r requirements.txt
				'''
			}
		}

		stage ('Run tests') {
			agent {
				docker {
					image 'python:3.10-slim'
				}
			}
			steps {
				sh '''
					pytest
				'''
			}
		}
		stage ('Package app') {
			agent {
				docker {
					image 'python:3.10-slim'
				}
			}
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