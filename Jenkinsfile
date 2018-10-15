pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
				sh 'docker build -t app:test .'
			}
		}
		stage('Test') {
			steps {
				echo 'TEST'
				sh 'docker run -d -p 80:80 --rm --name app app:test'
				sh 'nc -vz localhost 80'
				sh 'docker stop app'
			}
		}
		stage('Push Registry') {
			steps {
				sh 'docker tag app:test monicasatan/app:stable'
				sh 'docker push monicasatan/app:stable'
			}
		}
	}
}