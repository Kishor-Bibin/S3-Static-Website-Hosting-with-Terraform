

# S3 Static Website Hosting with Terraform

## Overview

This project demonstrates how to use **Terraform** to provision an **AWS S3 bucket** that serves as a static website. It includes the configuration of an S3 bucket with various essential resources, such as access control, bucket policies, and website configuration. The goal is to provide an automated way to set up and manage the infrastructure required for hosting static web content on AWS.

With this Terraform configuration, you can create an S3 bucket, set the appropriate permissions, upload essential files like an `index.html` and `error.html` page, and configure the bucket to serve a static website. It also includes key features like **public-read** access, bucket ownership controls, and custom error handling.

This project is ideal for anyone looking to automate the setup of a simple static website hosted on AWS S3 using **Infrastructure as Code (IaC)** principles.

---

## Key Features

- **S3 Bucket Creation**: Creates a fully functional AWS S3 bucket using Terraform.
- **Public Access Control**: Configures the bucket and objects for **public-read** access, making the files publicly accessible.
- **Static Website Configuration**: Configures the S3 bucket to act as a static website, with custom index and error pages.
- **File Upload**: Uploads essential static content, such as `index.html`, `error.html`, and `profile.png`, to the S3 bucket.
- **Bucket Ownership Controls**: Configures the bucket to prefer the bucket owner as the object owner, which helps ensure access management.
- **Environment Setup with Terraform**: Easily deploy and manage this setup using Terraform, allowing for repeatable and scalable infrastructure.

---

## Project Structure

This Terraform configuration includes the following components:

1. **S3 Bucket**: The primary storage for the static content.
2. **Access Control**: Public access control and ownership settings for the bucket and objects.
3. **Static Website Setup**: The configuration for enabling static website hosting, including error and index pages.
4. **S3 Objects**: The configuration to upload essential website files (`index.html`, `error.html`, and `profile.png`) into the bucket.

---

## Terraform Configuration Breakdown

### 1. **Creating an S3 Bucket**
The configuration creates an AWS S3 bucket by specifying a unique bucket name, which is passed via a variable. This bucket will hold all the static website content.

### 2. **Ownership Controls and Access**
- The bucket’s ownership controls are set to `BucketOwnerPreferred`, ensuring that the bucket owner maintains control over the objects.
- Public access settings allow for public-read permissions, meaning the uploaded files will be publicly accessible from the web.

### 3. **Configuring Bucket Permissions**
The bucket’s **Access Control List (ACL)** is configured with the `public-read` permission. This allows anyone on the internet to read the objects (files) within the bucket. 

### 4. **Uploading Static Files**
The following files are uploaded to the S3 bucket:
- **index.html**: The default landing page for the static website.
- **error.html**: A custom error page shown in case of issues like 404 errors.
- **profile.png**: An example image that can be used on the website.

### 5. **Static Website Hosting Setup**
The S3 bucket is configured as a **static website** by specifying the `index.html` as the homepage and `error.html` as the error page. This allows users to access the website directly via the bucket's website endpoint.

---

## Requirements

- **Terraform**: You need to have Terraform installed to manage and apply the infrastructure.
- **AWS Account**: An AWS account with sufficient permissions to create S3 resources.
- **AWS CLI Configured**: The AWS CLI should be configured with credentials that Terraform can use to provision the resources. Make sure your `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` are set up.

---

## Usage

### 1. **Clone the Repository**

First, clone the repository to your local machine:

```bash
git clone <repository-url>
cd <repository-directory>
```

### 2. **Define Variables**

The bucket name is provided as a **variable** (`var.bucketname`). You can either set it in a `terraform.tfvars` file, or directly in your Terraform configuration.

Example `terraform.tfvars`:

```hcl
bucketname = "my-unique-static-website-bucket"
```

### 3. **Initialize Terraform**

Run the following command to initialize the Terraform working directory:

```bash
terraform init
```

This will download the necessary provider plugins and set up the environment.

### 4. **Plan the Deployment**

Before applying any changes, it's a good practice to run the `terraform plan` command to preview what will be created or modified:

```bash
terraform plan
```

### 5. **Apply the Terraform Configuration**

Once you're satisfied with the plan, you can apply the configuration to create the resources:

```bash
terraform apply
```

Terraform will prompt you for confirmation. Type `yes` to proceed with the creation of the resources.

### 6. **Access the Website**

Once the deployment is complete, you can access the static website via the S3 bucket's **website endpoint**, which Terraform will output upon successful deployment. The endpoint will look something like:

```
http://<bucket-name>.s3-website-<region>.amazonaws.com
```

---

## Cleanup

To destroy the infrastructure and clean up the resources when you're done, use the following command:

```bash
terraform destroy
```

This will remove all the resources created by Terraform.

---

## Security Considerations

While this configuration allows public access to the S3 bucket and its objects, it's important to assess your security needs carefully. In production environments, you may want to restrict access or use more secure methods for controlling access to sensitive data.

- **Bucket ACLs**: Be cautious with `public-read` access. This configuration is ideal for a public website, but for private content, you should use more restrictive access controls.
- **Encryption**: For production environments, consider enabling encryption for both data at rest and in transit (e.g., using Amazon S3's server-side encryption features).

---

## Contributing

If you'd like to contribute to this project, feel free to fork the repository and submit a pull request with your changes. Suggestions, improvements, and bug fixes are always welcome!

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Conclusion

This project provides an easy-to-follow approach for provisioning an **AWS S3 static website** using **Terraform**. With this configuration, you can quickly deploy a static website to AWS, ensuring a consistent environment across all deployments, and manage your infrastructure as code. By using Terraform, you make your infrastructure repeatable, auditable, and scalable.

