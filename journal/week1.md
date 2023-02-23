# Week 1 — App Containerization

For the week 1 course, I was able to acheive the tasks listed below:

- Explore the codebases for the front end and backend services.

- Run the dockerfile CMD as an external script

- Used multi-stage building to build images.

- Ensured the apps were running locally without any issues.

- Created the Notification Section on the Cruddur Application.

- Tagged and Pushed images created  to DockerHub.

- Implemented healthcheck in the Docker compose file.

- Researched and implemented best practices of Dockerfiles in my Dockerfile

- Installed Docker on my localmachine and got the same containers running outside of Gitpod.

- Launched an EC2 instance with docker installed, and pulled a container to run my docker processes. 

## Built and Run Cruddur Website using multi-stage building to build images.

![Home Page](https://github.com/Damiloju123/aws-bootcamp-cruddur-2023/blob/18fca63e84c3e14af710318df133292046d0b7fd/_docs/assets/Home.JPG)

## Created the Notification Section on the Cruddur Application.

![Notifications Page](https://github.com/Damiloju123/aws-bootcamp-cruddur-2023/blob/18fca63e84c3e14af710318df133292046d0b7fd/_docs/assets/Notifications.JPG)

## Tagged and Pushed images created  to DockerHub.

Tagged my docker images with the Docker Tag command

![DockerHub](https://github.com/Damiloju123/aws-bootcamp-cruddur-2023/blob/18fca63e84c3e14af710318df133292046d0b7fd/_docs/assets/Docker.JPG)

## Implemented healthcheck in the Docker compose file.

This was done by adding the section below to each service in the Docker Compose file.

```sh
 healthcheck:
      test: ["CMD", "curl", "--fail", "http://localhost:4567"]
      interval: 10s
      timeout: 5s
      retries: 3
      start_period: 10s
    
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:3000"]
      interval: 10s
      timeout: 5s
      retries: 3
      start_period: 10s
      
    healthcheck:
      test: ["CMD", "curl", "--fail", "http://localhost:8000"]
      interval: 10s
      timeout: 5s
      retries: 3
      start_period: 10s

    healthcheck:
      test: nc -z localhost 5432 || exit -1
      interval: 10s
      timeout: 5s
      retries: 3
      start_period: 10s
```
![Health Status](https://github.com/Damiloju123/aws-bootcamp-cruddur-2023/blob/18fca63e84c3e14af710318df133292046d0b7fd/_docs/assets/Health%20Status.JPG)

## Launched an EC2 instance with docker installed, and pulled a container to run my docker processes. 

- Launched EC2 Instance via AWS Console

![EC2 Instance](https://github.com/Damiloju123/aws-bootcamp-cruddur-2023/blob/18fca63e84c3e14af710318df133292046d0b7fd/_docs/assets/EC2.JPG)

- Installed Docker 

![Docker](https://github.com/Damiloju123/aws-bootcamp-cruddur-2023/blob/18fca63e84c3e14af710318df133292046d0b7fd/_docs/assets/Docker%20Install.JPG)

- Pulled an image from Docker Hub

![Docker Image](https://github.com/Damiloju123/aws-bootcamp-cruddur-2023/blob/18fca63e84c3e14af710318df133292046d0b7fd/_docs/assets/Docker%20pull.JPG)
