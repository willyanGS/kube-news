pipeline {
    agent any

    stages {

        stage ('Build docker image') {
            steps {
                script {
                    dockerapp = docker.build("willyangs/kube-news:${env.BUILD_ID}", '-f ./src/Dockerfile ./src')
                }
            }
        }

        stage ('Push docker image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub')
                        dockerapp.push('latest')
                        dockerapp.push("${env.BUILD_ID}")
                }
            }
        }

        stage ('Deploy kubernetes') {
            environment {
                tag_version = "${env.BUILD_ID}"
            }
            steps {
                withKubeConfig ([credentialsId: 'kubeconfig']) {
                    sh 'sed -i "s/{{TAG}}/$tag_version/g" ./deployment-app.yaml'
                    sh 'kubectl apply -f ./deployment-app.yaml'
                }
            }
        }

    }
}