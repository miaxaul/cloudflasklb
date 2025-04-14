# 🌐 CloudFlaskLB – Flask App dengan IP Public  
👩‍💻 Author: https://github.com/miaxaul)

CloudFlaskLB adalah aplikasi sederhana berbasis **Flask** yang dijalankan di atas **Docker** dan dideploy ke **Amazon EC2** dengan **IP Public**. Proyek ini menampilkan bagaimana aplikasi containerized dapat dijalankan di AWS menggunakan ECR dan EC2.

---

## 📌 Fitur Proyek

- Custom **VPC** dengan public subnet
- Instance EC2 menggunakan **Amazon Linux**
- Akses aplikasi melalui **IP Public**
- Deployment menggunakan **Docker** dan image dari **Amazon ECR**

---

## 🧱 Infrastruktur

1. **VPC Setup**
   - VPC custom
   - 1 atau lebih subnet (public dan/atau private)
   - Route Table + Internet Gateway
   - NAT Gateway (jika perlu)
   - Security Group untuk EC2 dan EFS

2. **ECR**
   - Private repository bernama: `cloudflasklb-repo`

3. **IAM**
   - Instance EC2 menggunakan role: `LabInstanceProfile`

---

## 🚀 Deploy Aplikasi di EC2

### 1. Launch Instance

- AMI: Amazon Linux
- Subnet: Public
- IAM Role: `LabInstanceProfile`
- Security Group: Allow SSH (22) dan HTTP (80)

### 2. SSH ke Instance dan Setup:

```bash
sudo su
yum update -y
yum install git -y
git clone https://github.com/miaxaul/cloudflasklb.git
cd cloudflasklb
yum install -y docker
service docker start
systemctl enable docker
usermod -aG docker ec2-user
