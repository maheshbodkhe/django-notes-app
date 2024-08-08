pipeline {
    agent any
    
    stages{
        stage("Clone Code"){
            steps{
               echo "Cloning the code" 
               git url:"https://github.com/maheshbodkhe/django-notes-app.git", branch: "main"
            }
        }
         stage("Build"){
             steps{
                echo "Building the code"
                sh "docker build -t my-note-app ."
            }
        }
         stage("Push to Docker Hub"){
             steps{
               echo "Pushing the image to docker hub"
               withCredentials([usernamePassword(credentialsId:"DockerHub",passwordVariable:"DockerHubPass",usernameVariable:"DockerHubUser")]){
               sh "docker tag my-note-app ${env.DockerHubUser}/my-note-app:latest"
               sh "docker login -u ${env.DockerHubUser} -p ${env.DockerHubPass}"
               sh "docker push ${env.DockerHubUser}/my-note-app:latest"
               }
            }
        }
         stage("Deploy"){
             steps{
                echo "Deploying the container"
                sh "docker run -d -p 8000:8000 maheshbodkhe/my-note-app:latest"
            }
            
        }
    }
}
