![declaritive](https://github.com/user-attachments/assets/040ef7bd-1cb5-47ca-94ce-469760ccbcf6)


# Django Application on AWS with Jenkins Declarative CI/CD Pipeline
  ## Required tools for this project are:
    - AWS EC2 instance 🖥️
    - Docker 🐳
    - GitHub 🐙
    - Docker Compose 📦
    - Jenkins 🎛️
    - Java ☕
    
  ## Steps:

1. Create EC2 instance with ubuntu, t2.micro and storage volume of 8GB.

2. Edit security groups.

3. Open terminal and install docker.

4. Then install openjdk-17-jre and jenkins with following command

        - sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
        https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
       - echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
        https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
        /etc/apt/sources.list.d/jenkins.list > /dev/null
       - sudo apt-get update
       - sudo apt-get install jenkins

       - sudo usermod -aG docker $USER
       - sudo usermod -aG docker jenkins

6. Copy public IP of EC2 instance and paste it in new tab followed by :8080.

7. In EC2 instance terminal run below command to get password of jenkins. 
    sudo cat /var/lib/jenkins/secrets/initialAdminPassword

8. Enter password and do initial configuration of jenkins tool. And select 'install default plug-ins'.

9. Create pipeline

10. Go to pipeline configuration. And add your github url, branch name and jenkins filename where we are going to add declarative pipeline script.

11.  Need to add dockerhub credentials in jenkins configuration. Make sure the ID you are adding here, have to mention same in the pipeline scripting. 

12. Install docker-compose in EC2 terminal with command.
sudo apt-get install docker-compose

13. Need to write pipeline script for code checkout, image build, pushing to dockerhub and deploy. 

14. Then run the pipeline.


15. If it runs successfully, enter your public IP of EC2 instance in new tab followed by :8000.

And as shown below you will get "final deployed app" on your screen :) 

![1723109060289](https://github.com/user-attachments/assets/9260dcbb-ff6a-4570-ba8d-b889c7489149)



