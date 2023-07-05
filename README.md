# jenkin-CICD-pipline

## Jenkins CICD with GitHub Integration

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
4. Get You public ip and open on you bowser ip:8080
5. Jenkins page will open
6. get the jenkins password from
       - sudo cat /var/lib/jenkins/secrets/initialAdminPassword
7. Create user with the given credetials and save
8. Your jenkins app wil run
9. 
