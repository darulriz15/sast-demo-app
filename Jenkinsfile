pipeline {
	agent any

	stages {
		stage('Checkout') {
			steps {
				git url: 'https://github.com/darulriz15/sast-demo-app.git', branch: 'master'
			}
		}
		stage('Install Dependencies') {
			steps {
				sh 'python3 -m venv venv'
				sh '. venv/bin/activate'
				sh 'pip install --upgrade pip'
				sh 'pip install bandit'
			}
		}
		stage('SAST Analysis') {
			steps {
				sh '. venv/bin/activate
				sh 'bandit -f xml -o bandit-output.xml -r . || true'
			}
		}
	}
}
