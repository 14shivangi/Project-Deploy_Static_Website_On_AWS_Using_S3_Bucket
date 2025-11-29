# *SETUP OF TERRAFORM*


## Terraform Providers Section:

```
terraform {
  required_providers {
    aws = {
      source = "hashicorp/aws"
      version = "6.23.0"
    }
    random = {
        source = "hashicorp/random"
        version = "3.7.2"
    }
  }
}

provider "aws" {
  region = "ap-south-1"
}
```

## Creation of the Bucket:

<img width="1608" height="841" alt="Image" src="https://github.com/user-attachments/assets/27769fa0-f3a7-4008-a1a0-d18a4f415f3c" />

## Bucket Resourse - Terraform
```
resource "random_id" "randomid" {
    byte_length = 8
}

resource "aws_s3_bucket" "mybucket-website" {
  bucket = "mybucket-website-${random_id.randomid.hex}"
}

resource "aws_s3_bucket_public_access_block" "mybucket-website" {
  bucket = aws_s3_bucket.mybucket-website.id

  block_public_acls = false
  block_public_policy = false
  ignore_public_acls = false
  restrict_public_buckets = false

}
```


# BUCKET POLICY - Console

<img width="1919" height="890" alt="Image" src="https://github.com/user-attachments/assets/6702151a-cff6-43ab-9c6c-2c20a9e1e4d4" />


# BUCKET POLICY - Terraform
```
resource "aws_s3_bucket_policy" "mybucket-website" {
  bucket = aws_s3_bucket.mybucket-website.id
  policy = jsonencode(
    {
            Version = "2012-10-17",
            Statement =[
                {
                Sid = "PublicReadGetObject",
                Effect = "Allow",
                Principal = "*",
                Action = "s3:GetObject",
                Resource = "${aws_s3_bucket.mybucket-website.arn}/*"
                }
            ]
        }
    )
}
```




# **index.html* and **style.css* uploads through Terraform
<img width="1919" height="851" alt="Image" src="https://github.com/user-attachments/assets/1be0e799-e2a2-4bd4-b339-c3c5032297ac" />

# Through: Terraform 
```
resource "aws_s3_bucket_website_configuration" "mywebsite" {
  bucket = aws_s3_bucket.mybucket-website.id
  index_document {
    suffix = "index.html"
  }
}

resource "aws_s3_object" "index_html" {
  bucket       = aws_s3_bucket.mybucket-website.bucket
  source       = "./index.html"
  key          = "index.html"
  content_type = "text/html"
}

resource "aws_s3_object" "styles_css" {
  bucket       = aws_s3_bucket.mybucket-website.bucket
  source       = "./style.css"
  key          = "style.css"
  content_type = "text/css"
}
```
# Output link:

<img width="929" height="196" alt="Image" src="https://github.com/user-attachments/assets/e7f15ce9-cd96-414d-b337-8c2d22d3dbe3" />

# Output through Terraform: 
```
output "WebsiteLink" {
  value = aws_s3_bucket_website_configuration.mywebsite.website_endpoint
}
```
