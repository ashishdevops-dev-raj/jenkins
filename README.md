# Jenkins Installation on Ubuntu
----------------------------------------------------------------------------------------------------------------------------------------------------------

Step 1. Install OpenJDK

           sudo apt update && sudo apt install fontconfig openjdk-21-jre

Step 2: Install Jenkins

  2.1 Add Jenkins Repository Key
  
           sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  	   https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key

  2.2 Add Jenkins Repository
  
	echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  	https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  	/etc/apt/sources.list.d/jenkins.list > /dev/null

  2.3 Update Packages and Install Jenkins
  
           sudo apt-get update && sudo apt-get install jenkins


Step 3: Configure Inbound Rules

           Make sure port 8080 is open so you can access Jenkins.

Step 4: Start Jenkins and Unlock

  4.1 Get the Jenkins Initial Admin Password
  
          cat /var/lib/jenkins/secrets/initialAdminPassword
          
  4.2 Use This Password to Unlock Jenkins
  
         http://<your-server-ip>:8080


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------





# Jenkins Email Configuration Guide (Using Gmail SMTP)


Step 1: Enable 2-Step Verification on Gmail

	Go to your Gmail account.
 ![image](https://github.com/user-attachments/assets/57f4e7d3-2ebb-40a8-a0d9-5b3fe1daf2c0)


	Navigate to Manage Your Google Account.
	Click on Security.
 ![image](https://github.com/user-attachments/assets/e03f6b3f-e40b-458b-a88e-8186675bf2e0)

	Ensure 2-Step Verification is turned ON.

 ![image](https://github.com/user-attachments/assets/ea912cc2-adf6-436f-819b-f7fa11c85717)

 

Step 2: Generate an App Password

	In the Security section, search for App Passwords.
 ![image](https://github.com/user-attachments/assets/6712939d-0ee5-4105-80a0-524463ef14d8)

	Select App Passwords.
	Choose an app name (e.g., "Jenkins") and click Create.
 ![image](https://github.com/user-attachments/assets/4a793993-00c2-4701-8509-b0f4eeaefd76)

	Copy the generated password. You will use this later in Jenkins.

 ![image](https://github.com/user-attachments/assets/598929a5-235e-4d0b-b9c1-c4e01a810675)


 Step 3: Add Credentials in Jenkins
 
	Open Jenkins.
	Go to Manage Jenkins > Credentials.
![image](https://github.com/user-attachments/assets/2d11cb45-cc60-431b-986b-75c4294be1e7)

 
	Under Global credentials, click Add Credentials.
 ![image](https://github.com/user-attachments/assets/2f7ad3cc-a3b7-46e4-8561-3bd11fb53d80)

	For Username, enter your Gmail address.
 ![image](https://github.com/user-attachments/assets/0b4a6317-4227-46b2-8bf0-16fe74c28a57)

	For Password, paste the App Password you generated.
	ID: gmail-smtp-credentials (or a custom unique ID for scripting reference)
	Description: Credentials for sending email via Gmail SMTP
 ![image](https://github.com/user-attachments/assets/6e0168bd-14f4-4602-9a5e-526c13773bee)

	Save the credentials.
 
Step 4: Configure Email Settings in Jenkins

	Go to Manage Jenkins > Configure System.
 ![image](https://github.com/user-attachments/assets/c5422196-1699-4e32-bdfe-5f1315ec9322)

	Scroll to Extended E-mail Notification.
 ![image](https://github.com/user-attachments/assets/59ad5682-ee18-4165-8d5f-34eaa9a72355)

	Set the following:
		SMTP Server: smtp.gmail.com
		SMTP Port: 465
	Click Advanced and:
		Select Use SSL.
		Select the credentials you added earlier (your Gmail and App Password)
  ![image](https://github.com/user-attachments/assets/0186a968-e343-4e6a-8dd4-97b82dd48d15)


Step 5: Save and Test Configuration

	Save the configuration.
 ![image](https://github.com/user-attachments/assets/f33eb047-5d7d-47b2-892b-6ae37ae2c0fc)

	Test sending a test email to verify the setup is working.
 ![image](https://github.com/user-attachments/assets/878aa077-7d22-4a19-be06-3f3e54c63070)

	Email Extension Plugin

![image](https://github.com/user-attachments/assets/dab530b7-911f-4b71-a8a2-7e359a214454)




