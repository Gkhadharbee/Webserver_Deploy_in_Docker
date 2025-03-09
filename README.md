# <p align="">Simple WebServer with Docker
## <p align="">About the project</p>
   This project demonstrates how to create a simple web server with Docker. In this , we create a basic web server application and package it within a Docker container,
   allowing for easy deployment and management of your web service across different environments by leveraging Docker's containerization features.
   
![image](https://github.com/user-attachments/assets/55d631b4-e981-4d9d-b56f-b8d35c91d788)

## Overview

Create basic web server code that listens on a port and serves a basic HTML page when accessed. 
Write a Dockerfile, specify a base image and copy the web server code into the container.
Build the Docker Image and finally run the container using Docker commands.

## Pre-requisites

* AWS Prerequisites
* Install Docker
* Create a directory
* Create an index file
* Create a Dockerfile
* Build the docker image
* Start the container
* Allow the required port
* Access your web server

## <p align="">Steps</p>

### <p align="">Step1:</p>

#### <p align="">Launch the EC2 instance</p>

1. Set up an EC2 instance in an Amazon VPC by following below images.

![Screenshot 2025-02-23 153719](https://github.com/user-attachments/assets/a7982145-343a-481b-b282-2b565d446a73)

![Screenshot 2025-02-23 153735](https://github.com/user-attachments/assets/c290c7ef-74f7-4e70-8f48-0b51f8169234)

![Screenshot 2025-02-23 153752](https://github.com/user-attachments/assets/f2ababc3-8b04-429c-a2f9-e504a613d559)

![Screenshot 2025-02-23 153837](https://github.com/user-attachments/assets/5225db82-449b-4c3a-a031-c1d59ac9aae1)

2. Finally Launch the EC2 Instance.
3. Connect to the instance through the putty or through any terminal using Key pair.

### <p align="">Step2:</p>

#### <p align="">Install Docker</p>

1. After connecting to the instance, Install Docker using the following commands.
2. Before installing Docker, you should update the package index:
   
```bash
sudo yum update -y
```    

3. To install Docker on Amazon Linux, you can use the following command:

 ```bash
sudo yum install docker -y
```

4. After installing Docker, you will need to start the Docker service:

```bash
sudo systemctl start docker
```

5. Once you have started the Docker service, you can verify that it is running by running the following command in your terminal:

```bash
sudo docker run hello-world
```

6. If the installation is successful, you will see a message indicating that Docker is working correctly.
7. To start the Docker service automatically when the instance starts, you can use the following command:

```bash
sudo systemctl enable docker
```

8. Verify the Docker installation by running the Docker version command:

```bash
docker --version
```

### <p align="">Step3:</p>

#### <p align="">Create a Directory</p>

1. Create a directory for the web server project using below commands

```bash
mkdir nginx_image
cd nginx_image
```

2. Create another directory called files where we will store the index file and the dockerfile.

```bash
mkdir files
cd files
```

### <p align="">Step4:</p>

#### <p align="">Create Index file</p>

Create index file naming as index.html which contains html simple code.

```bash
vim index.html
```

![Screenshot 2025-02-25 133436](https://github.com/user-attachments/assets/4b46a5d4-90ff-4a84-a4a3-7ec86334a62a)

### <p align="">Step5:</p>

#### <p align="">Create Dockerfile</p>

Create a Dockerfile to specify the docker image.

```bash
FROM nginx
COPY index.html /usr/share/nginx/html/index.html
```

It helps to copy yhe index.html file into ngnix web server folder so that the web server can serve it to the users when they access the website.

![Screenshot 2025-02-24 124011](https://github.com/user-attachments/assets/4b45b5b3-b347-473f-9e3a-e7dd81ccffcf)

### <p align="">Step6:</p>

#### <p align="">Build Docker Image</p>

Build the Docker Image using docker commands

```bash
docker build -t my_web_server .
```

![Screenshot 2025-02-24 124011](https://github.com/user-attachments/assets/6ec8ca64-d5f8-4d6b-a237-6d511c136c9c)

### <p align="">Step7:</p>

#### <p align="">Start the container</p>
Run a docker container from image:

```bash
docker run -p 9090:80 my_web_server
```

![Screenshot 2025-02-24 123823](https://github.com/user-attachments/assets/7af5f05c-7ad9-48a7-8305-ecc76f6406ff)

### <p align="">Step8:</p>

#### <p align="">Allow the required port</p>

1. Allowing a port in the host system to communicate with a port in the Docker container.
2. To access the web server, you have to configure the security group linked with the EC2 instance running the docker container to permit incoming traffic on the port used by the web server.

![Screenshot 2025-02-24 125513](https://github.com/user-attachments/assets/71258931-5b1c-4efd-8898-1f9d3af074e2)

3. And save the changes in Inbound rules.

### <p align="">Step9:</p>

#### <p align="">Access the Web Server</p>

Open a web browser and go to “http://<public_ip_of_instance>:9090". You should see the message “Hello! Everyone, I am Khadhar Bee, This is my simple webserver with docker project”

![Screenshot 2025-02-24 123836](https://github.com/user-attachments/assets/4baf03c6-b6e2-4919-b504-b92ff0b811ba)
