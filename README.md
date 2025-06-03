# **Automated Online Boutique (11 Microservices)**  

## **Project Overview**  
This project showcases the deployment of an **AWS EKS-based cloud infrastructure** for an **online boutique** with **11 microservices**. The entire setup is automated using **Terraform, Helm, Jenkins, and Ansible**, ensuring seamless CI/CD workflows. **Prometheus & Grafana** provide monitoring and observability, while **S3** manages Terraform state.  

### **Tech Stack:**  
- **Infrastructure & Provision:** AWS-EKS, Terraform  
- **Deployment & Orchestration:**  Helm, Kubernetes
- **Automation:** Jenkins, Ansible, Bash  
- **Monitoring:** Prometheus, Grafana  
- **Storage:** Amazon S3  

---

## **Architecture Overview**  
This setup includes separate repositories for **application code**, **infrastructure provisioning**, and **Kubernetes deployment manifests**. Below is an **architecture diagram** illustrating the overall workflow:  

![Architecture Diagram](docs/images/architecture.png)  

**Workflow Overview:**  
1. **Development & CI/CD**: Jenkins automates builds, tests, and deployments.  
2. **Infrastructure Provisioning**: Terraform provisions AWS resources, and Ansible handles system configuration.  
3. **Microservices Deployment**: Kubernetes orchestrates containers using Helm charts.  
4. **Monitoring & Alerting**: Prometheus collects metrics, and Grafana visualizes system performance.  

---

## **Screenshots & Monitoring**  

### **Online Boutique UI**  
![Online Boutique Homepage](docs/images/boutique-ui.png)  

### **Prometheus Dashboard**  
![Prometheus Metrics](docs/images/prometheus-dashboard.png)  

### **Prometheus Query Metrics**  
![Prometheus Query Metrics Test](docs/images/query-metric.png)  

### **Grafana Monitoring**  
![Grafana Cluster Overview](docs/images/grafana-cluster.png)  

### **Node Exporter Dashboard**  
![Node Exporter](docs/images/node-exporter.png)  

### **Kubernetes Cluster**  
![Kubernetes Cluster Dashboard](docs/images/kubernetes-cluster.png)  

### **Alert Manager**  
![Alert Manager Test](docs/images/alert-manager-test.png)  


### **AWS Infrastructure Details**  
- **EKS Management Console**  
  ![AWS EKS Cluster](docs/images/aws-eks-console.png)  
- **S3 Terraform State Management**  
  ![Terraform State in S3](docs/images/aws-s3-state.png)  

---

## **Repository Structure & Links**  

Repository Structure
📂 micsvc-manifests/ →  Helm configurations for microservices deployment & Kubernetes YAML files for services, deployments, and monitoring
📂 infra-tf-pb/ →  Contains Terraform scripts for AWS provisioning & Stores playbooks for system setup & configuration
📂 micsvc-project/ → Holds CI/CD automation pipeline configuration

- **Application Repo** (Contains Jenkinsfile):  
  🔗 [micsvc-project](https://github.com/Osamaghorab/micsvc-project)  

- **Infrastructure Repo** (Terraform & Ansible for provisioning):  
  🔗 [infra-tf-pb](https://github.com/Osamaghorab/infra-tf-pb)  

- **Deployment Repo** (Kubernetes manifests & Helm charts):  
  🔗 [micsvc-manifests](https://github.com/Osamaghorab/micsvc-manifests)  


---

## **Setup & Deployment**  
### **Prerequisites**  
- AWS CLI & configured credentials  
- Terraform & Ansible installed  
- Kubernetes CLI (`kubectl`) & Helm  

### **Deployment Steps**  
1. **Clone repositories:**  
   ```sh
   git clone git@github.com:Osamaghorab/micsvc-project.git
   git clone git@github.com:Osamaghorab/infra-tf-pb.git
   git clone git@github.com:Osamaghorab/micsvc-manifests.git


- Clone the Original Microservices Repo:
This project is built upon the Google Cloud Microservices Demo. You can clone it for reference using:
git clone https://github.com/GoogleCloudPlatform/microservices-demo.git
- Note: The original repo is referenced here as an example but is not mandatory for this project's deployment.
Contributors & Credits- Original repo: Google Cloud Microservices Demo
- Built by Osama Ghorab