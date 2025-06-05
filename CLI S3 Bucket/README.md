# AWS S3 Bucket: Create, Upload, and Browse Using AWS CLI

# Prerequisites

•	AWS CLI installed (aws --version)
	•	AWS CLI configured (aws configure) with valid Access Key and Secret Key
	•	An IAM user with necessary S3 permissions
	•	A text file (e.g., sample.txt) ready for upload

## 1. Create an S3 Bucket

<img width="858" alt="s3-1" src="https://github.com/user-attachments/assets/89c82a49-54f6-4fa8-a590-68514bc5f94f" />

<img width="897" alt="s3-2" src="https://github.com/user-attachments/assets/9ca5a292-e29f-4d42-bb3a-b87b6c132d92" />

## 2. Upload a File to the Bucket

<img width="850" alt="s3-3" src="https://github.com/user-attachments/assets/e3906e03-b087-4af8-9fb2-8ebcb3f75a4a" />

## 3. Make the File Publicly Accessible

<img width="1106" alt="s3-4" src="https://github.com/user-attachments/assets/5fc509df-a166-474d-9103-c879acc77cb7" />

## 4. Access the File via Browser

<img width="1106" alt="s3-5" src="https://github.com/user-attachments/assets/c2c0c9f3-252d-4822-bbb0-e25031c38b52" />

#Conclusion

This task demonstrates how to create an Amazon S3 bucket using the AWS CLI, upload a sample text file, and make it publicly accessible over the internet. By using commands like aws s3api create-bucket and aws s3 cp, you can efficiently manage file storage from the command line. Instead of ACLs (which may be disabled by default), applying a bucket policy ensures secure and flexible public access. The uploaded file can then be accessed through a public S3 URL, making it ideal for static content hosting and easy data sharing.

