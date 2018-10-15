pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
				sh 'docker build -t app .'
			}
		}
		stage('Test') {
			steps {
				echo 'TEST'
				sh 'docker run -d app'
				sh 'nc -vz localhost 80'
				sh 'docker stop app'
			}
		}
		stage('Push Registry') {
			steps {
				sh 'docker tag app monicasatan/app:stable'
				sh 'docker push monicasatan/app:stable'
			}
		}
	}
}