# AWS_S3_static_website_deployment_with_custom_error_handling

## Overview
This project is a static website hosted on Amazon S3. It includes HTML & CSS for a clean, interactive, and visually appealing user experience. This site demonstrates basic S3 hosting, file uploads, and downloads, with a setup for handling errors with an error page.

## Features
- Responsive design with HTML and CSS.
- Hosted as a static website on AWS S3.
- Supports file upload and download.
- Custom error page (error.html) for file or page not found, with a button redirect to the home page (index.html).

## Prerequisites
- An AWS account.
- Basic knowledge of S3 and permissions.

## Installation & Setup

1. *Create an S3 Bucket*:
   - Go to the [S3 Management Console](https://aws.amazon.com/s3/).
   - Click on *Create Bucket*.
   - Enter a unique bucket name, select your preferred AWS region, and disable "Block all public access."
   - Acknowledge public access by checking the acknowledgment box, and click on *Create Bucket*.

2. *Enable Static Website Hosting*:
   - Go to your bucket's *Properties* tab.
   - Scroll to *Static Website Hosting* and enable it.
   - Set the *Index document* to index.html and *Error document* to error.html.
   - Save changes.

3. *Set Bucket Permissions*:
   - Navigate to the *Permissions* tab.
   - In *Bucket Policy*, paste the following policy, replacing <YOUR_BUCKET_NAME> with your actual bucket name:
     json
     ```bash
     {
       "Version": "2012-10-17",
       "Statement": [
         {
           "Effect": "Allow",
           "Principal": "*",
           "Action": "s3:GetObject",
           "Resource": "arn:aws:s3:::<YOUR_BUCKET_NAME>/*"
         }
       ]
     }
     ```
   - Click *Save* to apply the policy and make the bucket publicly accessible.

4. *Upload Files*:
   - Go to the *Objects* tab of your bucket and click on *Upload*.
   - Upload index.html, error.html, and any CSS for styling and interactivity.

## Usage
- Open the static website URL provided in the *Static Website Hosting* section of your S3 bucket properties to view the site.
- To test error handling, try accessing a non-existent file (e.g., https://your-bucket-name.s3-website.region.amazonaws.com/nonexistent-page) to see the error.html page.

## Configuration Notes
- *Default Encryption*: Enable server-side encryption for data protection.
- *Bucket Versioning*: Disable unless you need to keep multiple versions of objects.
- *Delete Policy*: Remember to empty the bucket before deleting it to avoid charges.

## Screenshots

### S3 Bucket Overview
![image](https://github.com/user-attachments/assets/fc7ff80b-2505-46d6-b3df-582b7482cd5b)


### Upload Interface
![Screenshot 2024-11-08 130232](https://github.com/user-attachments/assets/879425f4-85b0-4c9a-8b1c-607aee2bd17a)


### Home Page (index.html)
![Screenshot 2024-11-08 122145](https://github.com/user-attachments/assets/fde1adb2-d2c2-49b1-9540-a2cbf6b73b09)


### Error Page (error.html)
![Screenshot 2024-11-08 122210](https://github.com/user-attachments/assets/c84fd3d3-e299-4113-953b-661ee7496498)






