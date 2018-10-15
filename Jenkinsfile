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
				withCredentials([usernamePassword(credentialsId: 'db79aaf1-a215-4d5e-b590-638dc420f5f7', passwordVariable: 'GithubPass01', usernameVariable: 'monitasatan@gmail.com')]) {
					sh 'docker tag app:test monicasatan/app:stable'
					sh 'docker push monicasatan/app:stable'
				}
			}
		}
	}
}