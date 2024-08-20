
<a  align="center" name="readme-top"></a>


<!--  PROJECT LLOGO -->
<br />
<div align="center">
    <img src="https://github.com/user-attachments/assets/93433dcf-f7e7-4f96-9777-a90d18ff10c6" alt="Logo" width="100" height="100">


  <p align="center">
     Spring Cloud Microservices and Kubernetes .
    <br />
    <a href="https://github.com/benammarfares/K8s-Microservice-SpringCloud"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    ·
    <a href="https://github.com/benammarfares/K8s-Microservice-SpringCloud/issues/new?labels=bug&template=bug-report---.md">Report Bug</a>
    ·
  </p>
</div>



<!-- TABLEE OF CONTENTS -->
<!-- TABLEE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project
![Pull configuration (1)](https://github.com/user-attachments/assets/0b6f802b-cf68-4d7e-bb38-e8b6a6c2d5d6)

<br>

* This project have 7 services.<br>
* Assurance and AssurancePolicy that will store their data via Postgres .<br>
* Department and User that will store their data via H2 database. <br>
* Config-Server make eureka registration via config file on github that will be targeted by the application.yml .<br>
* Service-Registry will launch the eureka server.<br>

    
<p align="right">(<a href="#readme-top">back to top</a>)</p>



### Built With
<br>

* ![Spring](https://img.shields.io/badge/spring-%236DB33F.svg?style=for-the-badge&logo=spring&logoColor=white)
* ![Kubernetes](https://img.shields.io/badge/kubernetes-%23326ce5.svg?style=for-the-badge&logo=kubernetes&logoColor=white)
* ![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
* ![Apache Maven](https://img.shields.io/badge/Apache%20Maven-C71A36?style=for-the-badge&logo=Apache%20Maven&logoColor=white)

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- GETTING STARTED -->
## Getting Started
<br>

<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/a49c9837-c043-45e8-aee4-10820e76d51c" alt="kubectl get all">
</div>

* This project is based on microservice architecture and the objectif is to run the services on kubernetes :<br>
   * 1. Install minikube on your vm.<br>
   * 2. Install Docker on your vm <br>
      * Link Docker to the Minikube Driver cause minikube needs an hyperviser to run.<br>
   * 3. Create a directory on your vm that will have the (services,deployments,configMap,Secrets,StatefulSet) yml files<br>
   * 4. Now you can run the minikube and enter the direcotory and run all the files with a simple commands.<br>
* For testing, I installed Postman for linux . <br>

### Prerequisites

* Virtual Machine
* Java 17 
* All the dependicies are included in the pom.xml no need to worry
    * Spring Boot Actuator
    * Eureka Discovery Client
    * Eureka Server
    * Gateway
    * Lombok
    * Spring Data JPA
    * PostgresSQLDriver
    * OpenFeign...
* Docker
* Minikube
* Postgres (it will be pulled automatically when you run the yml files on the vm directory)
  
  
### Installation

1. Clone the repo
   ```sh
   git clone https://github.com/benammarfares/K8s-Microservice-SpringCloud.git
   ```
2. Now let's go threw how to run all this : After the required installation .
   ```sh
   minikube start --driver==docker
   ```   
3. Minikube comes with the kubectl dependency so all you need to do so you can use the kubectl command is .
   ```sh
   alias kubectl="minikube kubectl --"
   ```
4. Enter the directory where you pulled all the yml files you need to launch your pods  .
   ```sh
   cd Name-your-directory"
   ```
5. To run your cluster you will need to launch this command  :
   ```sh
   kubectl applt -f ./
   ```
6. To inspect :
   ```sh
   kubectl get all
   ```
7. After you get all your pods running to access the eureka and inspect if all the services has regiestered ,run this command:
   ```sh
   minikube  service eureka-lb
   ```
   * It will give you a link to the eureka server .
     
8. Note that all the api's will be processed by the gateway that play a LoadBalancer role so you will need to expose it :
   ```sh
   minikube  service cloud-gateway-svc
   ```
9. Now you can test your api by using Postman
   
<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- CONTACT -->
## Contact

 <a href="https://www.linkedin.com/in/fares-ben-ammar-14b8b3226/">
                <img alt="LinkedIn" title="Discord" src="https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white"/></a> 
    <a href="https://www.instagram.com/fares.ben.ammar/?hl=fr">
                <img alt="Instagram" title="Instagram" src="https://img.shields.io/badge/Instagram-%23E4405F.svg?style=for-the-badge&logo=Instagram&logoColor=white"/></a>
        <a href="https://discord.gg/farou1747">
                    <img alt="Discord" title="Discord" src="https://img.shields.io/badge/Discord-%235865F2.svg?style=for-the-badge&logo=discord&logoColor=white"/></a> 
            <a href="https://facebook.com/https://www.facebook.com/faroutiti.benammar/">
                    <img alt="Facebook" title="Facebook" src="https://img.shields.io/badge/Facebook-%231877F2.svg?style=for-the-badge&logo=Facebook&logoColor=white"/></a> 
    <a href="mailto:benammar.Fares@esprit.tn">
    <img alt="Outlook" title="Outlook" src="https://img.shields.io/badge/Microsoft_Outlook-0078D4?style=for-the-badge&logo=microsoft-outlook&logoColor=white"/>



<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

Important to who will start from scratch !!!! :)

- [Spring Developer](https://www.youtube.com/@SpringSourceDev)
- [Josh Long](https://www.youtube.com/@coffeesoftware)
- [DaShaun Carter](https://www.youtube.com/@dashaun)
- [Spring Boot Learning](https://www.youtube.com/@SpringBootLearning)
- [Spring Tips](https://www.youtube.com/playlist?list=PLgGXSWYM2FpPw8rV0tZoMiJYSCiLhPnOc)
- [Amigoscode](https://www.youtube.com/@amigoscode)
- [Java Brains](https://www.youtube.com/c/JavaBrainsChannel)
- [Daily Code Buffer](https://www.youtube.com/@DailyCodeBuffer)




