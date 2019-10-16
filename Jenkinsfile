pipeline {
	agent any
	stages {
		stage('"Lint"') {
			steps{
				sh 'make lint'
			}
		}

		stage('Docker Build') {
            steps {
                sh 'docker build -t yproskurina/prediction-app:$BUILD_NUMBER'
            }
        }

        stage('Docker Push') {
          steps {
            withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
              sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
              sh 'docker push yproskurina/prediction-app:$BUILD_NUMBER'
            }
          }
        }

         stage('Docker Push') {
           steps {
             withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
               sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
               sh 'docker push yproskurina/prediction-app:$BUILD_NUMBER'
             }
           }
         }
	}
}
