# AREP LAB6: Secure Application Design

### Workshop Summary: Secure Application Design

In this workshop you will find how to design and deploy a secure and scalable application using AWS. The focus will be on implementing best security practices across two main components Server 1: Apache Server and Server 2: Spring Framework.

You will learn how to integrate security measures, configure multi-server deployments, and utilize modern encryption techniques to safeguard user data.


## Project Summary

1. **Server 1: Apache Server**
   - Serve an asynchronous HTML+JavaScript client over a secure TLS connection.
   - Ensure client-side code is delivered through encrypted channels for data integrity and confidentiality.

2. **Server 2: Spring Framework**
   - Handle backend services with RESTful API endpoints protected by TLS.
   - Facilitate secure communication between the client and the backend.

### Key Security Features to Implement:
- **TLS Encryption**: Use Let’s Encrypt for generating TLS certificates to ensure secure data transmission.
- **Asynchronous Client**: Optimize performance using async techniques while maintaining secure communication.
- **Login Security**: Implement authentication with securely hashed passwords.
- **AWS Deployment**: Deploy and manage all services on AWS.

## Getting Started
These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

Before install and run the project you will need:

1. **Java** (version 17)

2. **Maven** (version 3.9.9)
    - Download Maven from [here](http://maven.apache.org/download.html)
    - Follow the installation instructions [here](http://maven.apache.org/download.html#Installation)

3. **Git**
    - Install Git by following the instructions [here](http://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

4. **MySQL Server** 


### Installing

1. **Clone the repository and navigate into the project directory**:
    ```sh
    git clone https://github.com/JuanDavidGarciaPulido/AREP_LAB6.git

    cd AREP_LAB6
    ```

2. **Compile the project**:
   ```sh
   mvn clean install
   ```

3. Set up the database:
   - Create a new MySQL database named `property_management`
   - Update `application.properties` in the `src/main/resources` directory with your database credentials

4. Run the backend:
   ```
   mvn spring-boot:run
   ```
5. Access the application at:
   `http://localhost:8080`

## Running the tests

To run the automated tests you'll have to type in the console
```
mvn test
```

![image](https://github.com/user-attachments/assets/526a71d9-50c7-4601-921e-9547a2b82248)



## Deployment Instructions

### 1. Frontend Deployment
   - **Environment**: Deploy the static HTML and JavaScript files on an Amazon EC2 instance running Apache.
   - **Steps**:
     1. Install Apache on the instance.
     2. Place the frontend files in the web server's document root (`/var/www/html`).
     3. Configure TLS with Let's Encrypt:
        - Install Certbot.
        - Generate and install the certificate.
        - Verify that HTTPS is enabled for the domain.

### 2. Backend Deployment
   - **Environment**: Deploy the Spring Boot application on a separate EC2 instance with .
   - **Steps**:
     1. Install Java 17, Maven 3.8.4 and Git on the instance.
     2. Clone the repository
        
        ```
        git clone https://github.com/bricenojuliana/AREP-lab-security
        ```
        
     4. Compile the application
        ```
        mvn clean install
        ```
     6. Run the backend application (`.jar` file).
        ```
        sudo java -jar target/jpa-0.0.1-SNAPSHOT.jar
        ```
     7. Set up TLS using Let's Encrypt:
        - Install Certbot.
        - Use Certbot to create and install certificates for the backend.

### 3. Database Deployment
   - **Environment**: Use the previous instance.
   - **Steps**:
     1. Install MySQL server.
     2. Configure the database schema for user authentication and property management.
     3. Secure the MySQL instance by allowing access with a special user.


## Requirements

- **Amazon EC2 Instances**

- **Software Dependencies**:
  - Apache (for serving the frontend).
  - Java 17 (backend).
  - MySQL (database).
  - Certbot (for TLS configuration with Let's Encrypt).


## Usage

https://github.com/user-attachments/assets/406d2e93-18d3-4dc8-9dc6-bf9524dae4e8

### Architecture Diagram

![image](https://github.com/user-attachments/assets/91fd6f34-46a8-49d4-8202-e46a2b2bcc98)


## System Architecture

The system has three main components:

1. **Frontend**: 
   - Built with HTML, CSS, and JavaScript, the frontend allows users to interact with the system. It provides forms for modificating propierties.

2. **Backend**:
   - Developed with java and Spring Boot, the backend exposes RESTful endpoints for each CRUD operation.
     
3. **Database**:
   - A MySQL database is used to store property information.

## Class Design

### Main Classes

1. **Property**
   - Attributes: 
     - `id`: Long 
     - `address`: String
     - `price`: Double
     - `size`: Double
     - `description`: String

2. **PropertyService**
   - Responsible for handling business logic related to property management, including CRUD operations.

3. **PropertyController**
   - Exposes RESTful endpoints for the frontend to interact with the property data.

4. **PropertyRepository**
   - Interfaces with the database to perform CRUD operations on property listings.

## Author
This project was developed by Juan David García Pulido.

## Date

Friday, October 18 - 2024

## License

This project is licensed under the GNU license; See the [LICENSE.txt](LICENSE.txt) file for details.