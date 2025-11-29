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
# *Configuration: 

<img width="950" height="700" alt="Image" src="https://github.com/user-attachments/assets/8c0a2cb4-c2c1-45eb-aa71-93b3381fa554" />


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
<img width="950" height="700" alt="Image" src="https://github.com/user-attachments/assets/9fbbe295-ff58-485f-be6a-907ad22d20d3" />

```
terraform destroy
```

