# jenkin-CICD-pipline


![Untitled Diagram (1)](https://github.com/SachinBorse009/jenkin-CICD-pipline/assets/111965224/6a98cd8b-d393-40f6-83fc-5036d6891c8c)


## Jenkins CICD with GitHub Integration

### Prerequsite
   - AWS account
   - AWS EC2 instance
   - Linux
   - Github
   - And having knowledge about how to run the project (such as Node.js, Django, Java, etc.) is not necessary. However, in case the GitHub repository doesn't have a readme file explaining how to run the project

## Follw the Steps 

   1. Create AWS EC2 instance
      - Lunch AWS EC 2 instance
   2. Install Jenkins on AWS
      - Step1 : Install Java
           ```
          sudo apt update
           ```
           ```
          sudo apt install openjdk-11-jre
           ```
           ```
          java -version
           ```
       - Step2 : Install Jenkins
            ```
           curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
            /usr/share/keyrings/jenkins-keyring.asc > /dev/null
            ```
            ```
           echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
            https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
            /etc/apt/sources.list.d/jenkins.list > /dev/nul
            ```
            ```
           sudo apt-get update
            ```
            ```
           sudo apt-get install jenkins
            ```
       - Step3 : Start Jenkins
            ```
           sudo systemctl enable jenkins
            ```
            ```
           sudo systemctl start jenkins
            ```
            ```
           sudo systemctl status jenkins
            ```
   3. The jenkins run on port 80 so we have open port 8080 on our EC2 instance.
      - open EC2  Security and go to secuity groups link
      - Edit Inbound rules
      - Add rules
      - Select Type - Custom TCP
      - Port range - 8080
      - Souce - MyIp
   5. Get You public ip and open on you bowser ip:8080
   6. Jenkins page will open
   7. get the jenkins password from
          - sudo cat /var/lib/jenkins/secrets/initialAdminPassword
   8. Install plugins
   9. Create user with the given credetials and save
   10. Your jenkins app wil run

### Jenkins
   1. Create a new job
   2. fill the details
         - Enter an item name
         - Select Freestyle project
         - Click Ok
   3. Write a Description about you project
   4. Source Code Management - Git
         - Github repository URL
         - Credential
         -    - Go to EC2 instance
              - create SSH key 
              ```
              ssh-keygen
              ```
              ```
              cd .ssh/
              ```
              ```
              sudo cat id_rsa #this is your private key
              ```
              ```
              sudo cat id_rsa.pub # this is your public key
              ```
         - #### Github
         - Go to the github setting
         - click on ssh and GPG key
         - click new ssh key
         - Name it and paste a public key which is generete on EC2 id_rsa.pub
         - save it
         - Then, Back to jenkins where we left the Source Code Management Git
         - In Credential Add/jenins.The new window pop up (jenkins credential Provider:Jenkins)
              - Domain : as it is
              - Kind : select SSH Uername with private key
              - Scope : as it is
              - ID : you can give any ID (like jenkins-git)
              - Description: details about pipline
              - Username : Fill username which is on your EC2 instance(like, ubuntu)
              - private key : Paste private key which is created on EC2 id_rsa
              - and Add
         - Branches to Build : This info you can take it form github repo which you want to ntegration like master, main, or any other branch name name it like */main
         -  Rest of the will as it is
         -  save
         -  Buld Now
         -  pipline successfull run if not then check the erros from console output
   5. Then go to EC2 instance check the path of your project file from console output
   6. Go to that directory and then run that project as per the project run instructions
   7. After installing all the packeges and dependecies for the project then run the project and see on which port are running the porject. let say my project it running on 8000 port then you have to expose that port on you EC2 machiche.
   8. #### Expose the port
         - Got to EC2 instnce
         - security groups
         - add inboud rules
         - add rules
         - custom TCP
         - port 8000 for my project you can enter the port number as per you project
         - ip Anywehre IPV4
         - save it
     
   9. Go to browser and paste your EC2 machine public ip and port number(ip:8000)
   10. your project runnig.........
   11. Hurry the jenkins pipeline created successfully

## Thank you 

