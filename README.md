# 🚀 Cloud Observability Automation using Terraform

This project demonstrates **automated cloud monitoring and observability** by provisioning AWS infrastructure with **Terraform** and configuring two parallel monitoring approaches:  

1. **AWS Native Monitoring (CloudWatch + SNS)**  
   - CloudWatch Dashboard for EC2 metrics (CPU Utilization).  
   - CloudWatch Alarm integrated with SNS to send email alerts when CPU utilization exceeds **80%**.  

2. **Open-Source Monitoring Stack (Prometheus, Node Exporter, Grafana)**  
   - Prometheus collects metrics.  
   - Node Exporter exposes system-level metrics (CPU, memory, disk, network).  
   - Grafana provides interactive dashboards for real-time visualization.
   

---

## 🛠️ Key Skills & Tools
- **AWS**: VPC, Subnet, Internet Gateway, Route Table, Security Groups, EC2, CloudWatch, SNS  
- **Terraform (IaC)**: Infrastructure as Code automation  
- **Monitoring Stack**: Prometheus, Node Exporter, Grafana  
- **Linux & Bash**: Automated installation via user data script  
- **Security**: Restricted SSH access (specific CIDR / intra-VPC), firewall rules  

---

## ⚙️ Infrastructure Setup
Terraform provisions a secure AWS environment:  
- **VPC** with CIDR block `10.0.0.0/16`  
- **Public Subnet** with auto-assigned public IPs  
- **Internet Gateway + Route Table** for internet access  
- **Security Groups** allowing ICMP, HTTP (80), SSH (22 from specific IP), Prometheus (9090), Grafana (3000)  

---

## 💻 Instance Setup
An **EC2 instance** is provisioned with `user_data` automation that installs:  
<img width="1913" height="912" alt="ssh-jump-server" src="https://github.com/user-attachments/assets/6696701d-6ada-4db3-82e7-3078b31a2f64" />
- **Prometheus** (monitoring & metrics scraping)  
- **Node Exporter** (host-level metrics)  
- **Grafana** (dashboards & visualization)  
 <img width="1918" height="1012" alt="Grafana" src="https://github.com/user-attachments/assets/7a024488-ff8f-44f9-967c-7ea2ff1413fa" />
 
---

## 📊 CloudWatch Dashboard & Alerts
- **Dashboard** tracks EC2 CPU utilization with both graph & single-value widgets.
- <img width="1917" height="952" alt="CLOUDWATCH-DashBoard" src="https://github.com/user-attachments/assets/40b778f6-f713-43d5-8079-13e94e38504d" />
- **Alarm** triggers when CPU usage ≥ **80%**.
-  <img width="1907" height="967" alt="ALERT-DASHBOARD" src="https://github.com/user-attachments/assets/d8b0fbdd-f12c-48df-bcbd-d0768403a3db" />
- **SNS Integration** delivers proactive email notifications.
- <img width="1500" height="455" alt="SNS" src="https://github.com/user-attachments/assets/31c4ceaa-0851-4660-9815-c41213ecb3f6" />


---

## 🔒 Security Considerations
- SSH restricted to a specific CIDR or intra-VPC instances.  
- Monitoring ports intentionally exposed for dashboards.  
- Services run with least privilege (e.g., Node Exporter user).  

---

## 🧹 Resource Cleanup
To safely remove all resources and avoid unwanted AWS charges:  

```bash
terraform destroy -auto-approve


