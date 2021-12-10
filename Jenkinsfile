def containerName="docker-pipeline"
def dockerHubUser="511993"
def httpPort="8090"

node {

    stage('Checkout') {
        checkout scm
    }

    stage('Deploy to Kubernetes'){
        withCredentials([usernamePassword(credentialsId: 'dockerHubAccount', usernameVariable: 'dockerUser', passwordVariable: 'dockerPassword')]) {
            sh "docker login -u $dockerUser -p $dockerPassword"
			sh "kubectl get deployments"
			sh "helm list"
		sh "helm upgrade --install ${containerName} ./counterwebapp --set image.name=${dockerHubUser}/${containerName} --set image.tag=${tag}"
        }
    }
}
