#  *🚀Project-Deploy Static Website On AWS S3 Bucket Using TerraForm*

This project demonstrates how to deploy a fully static website (HTML + CSS) on an AWS S3 Bucket using Terraform.  
It includes bucket creation, public access configuration, website hosting setup, and automatic upload of site files.
---

##  Project Overview
This Terraform project automates the deployment of a static website on AWS S3.  
It provisions:

- S3 bucket (with a unique name)
- Public access configuration
- Bucket website hosting
- Uploads `index.html` and `style.css`
- Outputs the live website endpoint
---

## 📁 Project Structure
- main.tf
- index.html
- style.css
---

##  Prerequisites:
Make sure you have:
- AWS CLI configured (`aws configure`)
- Terraform installed (v1.0+)
- An AWS account with S3 permissions
---

##  How to Use
- Initialize Terraform
```
terraform init
```
```
terraform validate
```
```
terraform apply
```
<img width="790" height="1040" alt="Image" src="https://github.com/user-attachments/assets/a9b44129-9fa6-4cc1-a286-885323acde32" />

```
terraform destroy
```
<img width="700" height="500" alt="Image" src="https://github.com/user-attachments/assets/41d55fa0-0536-4045-9c68-9cd0a703eb05" />
