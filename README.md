# Automated Deployment Demo

A beginner-friendly Java web application project for practicing CI/CD with GitHub, Jenkins, Maven, AWS EC2, and Apache Tomcat.

## Architecture

Developer → GitHub → Jenkins → Maven package (`sample.war`) → Apache Tomcat → Browser

## Prerequisites

- Java JDK compatible with the installed Jenkins/Maven setup
- Maven
- Git and a GitHub account
- Jenkins
- Apache Tomcat 9

## Build locally

From the project root, run:

```bash
mvn clean package
```

The WAR file should be generated at:

```text
target/sample.war
```

## Deploy with the existing Jenkins job

The current Jenkins job can be configured to build this repository with Maven and deploy `target/sample.war` using the Jenkins Deploy to container plugin. Configure the Tomcat URL and credentials in Jenkins; do not store passwords in this repository.

For the setup described in the project practice, the Tomcat Manager Text URL is:

```text
http://YOUR_EC2_PUBLIC_IP:8081/manager/text
```

Replace `YOUR_EC2_PUBLIC_IP` with the instance's current public IP. Ensure the EC2 security group allows port 8081 only from trusted IP addresses, and ensure Tomcat Manager access is configured securely.

## Verify

After deployment, open:

```text
http://YOUR_EC2_PUBLIC_IP:8081/sample/
```

Replace the placeholder with the current public IP.

## Important security notes

- Never commit AWS access keys, passwords, private keys, or Jenkins secrets.
- Do not use default or example Tomcat passwords.
- Restrict inbound access to Jenkins and Tomcat ports to trusted IP addresses.
- This is a personal learning project, not a production deployment.
