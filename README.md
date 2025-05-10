# Jenkins Installation on Ubuntu


Step 1. Install OpenJDK
           $ sudo apt update && sudo apt install fontconfig openjdk-21-jre

Step 2: Install Jenkins
  2.1 Add Jenkins Repository Key
           $ sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \ https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key

  2.2 Add Jenkins Repository
	         $ echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \ https://pkg.jenkins.io/debian-stable binary/ | sudo tee \ /etc/apt/sources.list.d/jenkins.list > /dev/null

  2.3 Update Packages and Install Jenkins
           $ sudo apt-get update && sudo apt-get install jenkins


Step 3: Configure Inbound Rules
           Make sure port 8080 is open so you can access Jenkins.

Step 4: Start Jenkins and Unlock
  4.1 Get the Jenkins Initial Admin Password
          $ cat /var/lib/jenkins/secrets/initialAdminPassword
          
  4.2 Use This Password to Unlock Jenkins
         http://<your-server-ip>:8080




