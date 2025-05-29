## **Project Overview**
Automated the local deployment of a Java-based social networking site. The application consists of a 3-tier architecture with load balancing, caching, message queuing, and persistent storage.

## **Technologies Used**
- Java (App)
- Apache Tomcat (Web App Server)
- NGINX (Load Balancer)
- MySQL (Database)
- RabbitMQ (Messaging Queue)
- Memcached (Caching)
- NFS (Shared Storage)
- Vagrant + VirtualBox (IaC & VM Automation)
- Git, Git Bash, VSCode, IntelliJ IDEA
- Chocolatey (Windows package manager)
- AWS Certificate Manager
- Docker, DockerHub, SonarCloud

## **Problem Statement**
Setting up a multi-service Java web application locally is complex and error-prone. Manual configuration was not repeatable and slowed down development cycles.

## **Solution Implemented**
Automated provisioning using Vagrant and shell scripts to spin up all required services inside VirtualBox-managed VMs. Each tier of the application runs on an isolated VM, improving modularity, repeatability, and speed of setup.

## **Architecture Overview**
Users → NGINX Load Balancer → Apache Tomcat (App) → MySQL, RabbitMQ, Memcached → NFS

## **Automated Setup Flow**
1. Install prerequisites (Docker, VirtualBox, Vagrant, Git, IDEs, etc.) via Chocolatey or bash script.
2. Clone the GitHub repo: https://github.com/sean-njela/sample_java_app
3. Navigate to the Vagrant folder with the `Vagrantfile`
4. Run `vagrant up` to provision VMs: (Same files are used to provision with docker)
   - db01 (MySQL)
   - mc01 (Memcached)
   - rmq01 (RabbitMQ)
   - app01 (Tomcat)
   - web01 (NGINX)
5. Each VM runs a provisioning shell script (e.g., `mysql.sh`, `nginx.sh`) to install and configure services
6. Verify the application via the web browser on NGINX VM’s IP (port 80)

## **Vagrant Plugin**
Installed `vagrant-hostmanager` to auto-manage /etc/hosts for easy hostname access

## **Scripts Used**
Custom scripts to automate tool installation, service configuration, and application deployment

## **Results Achieved**
- Setup time reduced from hours to ~20 mins
- Fully automated and repeatable environment
- Enabled seamless R&D, debugging, and demos

## **Key Learnings**
- Practical use of Infrastructure as Code (IaC)
- Proficiency in Vagrant and service configuration with bash
- Architecture design for distributed systems

## **Next Steps**
- Containerize each service with Docker
- Deploy to cloud using Terraform and Ansible

## **Conclusion**
This automation approach provides a scalable and maintainable way to replicate complex production-like environments for local testing and development.
