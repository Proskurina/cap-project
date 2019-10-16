pipeline {
	agent any
	stages {
		stage('"Lint"') {
			steps{
				sh 'echo "Some tests here"'
			}
		}

		stage('Docker Build') {
            steps {
                sh 'sudo docker build --tag=prediction-app .'
            }
        }

        stage('Docker Push') {
          steps {
            withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
              sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
              sh 'docker tag prediction-app yproskurina/prediction-app:$BUILD_NUMBER'
              sh 'docker push yproskurina/prediction-app:$BUILD_NUMBER'
            }
          }
        }

         stage('Kube Push') {
           steps {
             withCredentials([usernamePassword(credentialsId: 'k8secret', passwordVariable: 'k8secretPassword', usernameVariable: 'k8secretUser')]) {
               sh "kubectl run prediction-app --image=$dockerpath:$BUILD_NUMBER --port=80"
               sh 'kubectl get pods'
             }
           }
         }
	}
}
