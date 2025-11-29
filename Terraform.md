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

- BUCKET POLICY
<img width="1919" height="890" alt="Image" src="https://github.com/user-attachments/assets/6702151a-cff6-43ab-9c6c-2c20a9e1e4d4" />


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

output "WebsiteLink" {
  value = aws_s3_bucket_website_configuration.mywebsite.website_endpoint
}
