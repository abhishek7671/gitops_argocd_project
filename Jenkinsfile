pipeline{
    agent any
    environment{
        DOCKERHUB_USERNAME= "abhisuda201"
        APP_NAME = "gitops-argo-app"
        IMAGE_TAG = "${BUILD_NUMBER}"
        IMAGE_NAME = "${DOCKERHUB_USERNAME}"+"/" + "${APP_NAME}"
        REGISTRY_CREDS = 'dockerhub'
    }
    stages{
        stage('Cleanup workspace'){
            steps{
                script{
                    cleanws()
                }
            }
        }

        stage('checkout SCM'){
            steps{
                script{
                    git credentialsId: 'github',
                    url: 'https://github.com/abhishek7671/cicd.git',
                    branch : 'main'
                }
            }
        }
        stage('Build Docker Image'){
            steps{
                script{
                    docker_image = docker.build "${IMAGE_NAME}"
                }
            }
        }
    }
}








//  pipeline {
//     environment {
//         imagename = "ganeshpoloju/jenkinss"
//         dockerImage = ''
//         containerName = 'my-container'
//         dockerHubCredentials = 'admin'
//     }
 
//     agent any
 
//     stages {
//         stage('Cloning Git') {
//             steps {
//                 git([url: 'https://github.com/GANESH0369/jenkins.git', branch: 'main'])
//             }
//         }
 
//         stage('Building image') {
//             steps {
//                 script {
//                     dockerImage = docker.build "${imagename}:latest"
//                 }
//             }
//         }
 
//         stage('Running image') {
//             steps {
//                 script {
//                     sh "docker run -d --name ${containerName} ${imagename}:latest"
//                     // Perform any additional steps needed while the container is running
//                 }
//             }
//         }
 
//         stage('Stop and Remove Container') {
//             steps {
//                 script {
//                     sh "docker stop ${containerName} || true"
//                     sh "docker rm ${containerName} || true"
//                 }
//             }
//         }
 
//         stage('Deploy Image') {
//             steps {
//                 script {
//                     // Use Jenkins credentials for Docker Hub login
//                     withCredentials([usernamePassword(credentialsId: dockerHubCredentials, usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
//                         sh "docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD"
 
//                         // Push the image
//                         sh "docker push ${imagename}:latest"
//                     }
//                 }
//             }
//         }
//     }
// }