# **🌍 TravelHUB – Static Website Hosting Using Amazon S3 and CloudFront CDN**

### ▶️ Watch the Project:

[![Video](https://img.youtube.com/vi/abcd1234/0.jpg)](https://youtu.be/I46WVfJkkbA)



A fully responsive static travel website deployed using Amazon S3 and secured globally using Amazon CloudFront.

**📌 About the Project**

TravelHub is a sleek, modern, and performance-oriented travel website designed to provide a seamless browsing experience for users exploring destinations, hotels, activities, and travel inspirations.

This project demonstrates:

- Frontend development fundamentals

- Modern build tools (Vite)

- Cloud hosting using AWS services

- Static site delivery at scale

- Best practices in S3 public hosting + CloudFront security



**✨ Key Features**
*🌐 Modern User Interface*

- Clean, responsive design optimized for all devices

- Intuitive navigation and layout

- Interactive components and smooth transitions

**🏨 Hotel & Destination Sections**

- Dynamic visual sections for hotels and travel spots

- Easily customizable pricing and content

**🔒 Secure Global Deployment**

- Hosted in an S3 Static Website Hosting bucket

- Secured using CloudFront, enabling full HTTPS

- Edge caching ensures sub-second global delivery


**🏗️ Project Architecture**
```
Frontend 
     ⬇
Amazon S3 Bucket
(Static Website Hosting Enabled)
     ⬇
CloudFront CDN
(HTTPS + Global Acceleration)
     ⬇
End Users
```


#### **☁️ AWS Deployment Breakdown**

**🪣 Amazon S3 — Static Hosting**

The website's dist/ folder is uploaded into an S3 bucket configured for static hosting.

🔹 Why Static Website Hosting?

- S3 can host HTML, CSS, JS directly

- No backend server required

- Highly scalable and cost-efficient

**🔹 Why Uncheck Block All Public Access?**

S3 blocks public access by default for security.
But a public-facing website must be accessible to everyone.
We uncheck it only for this bucket because it contains public frontend assets, not sensitive data.

**🔹 Why Add a Bucket Policy?**

Even after allowing public access, AWS still protects the bucket.
A bucket policy explicitly gives read-only access to all users:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::your-bucket-name/*"
    }
  ]
}
```

This ensures:

- Only GET requests are allowed

- No write or delete operations

- Safe for static content



### ***🌐 Amazon CloudFront — Global CDN + HTTPS***

S3 website endpoints only support **HTTP**, which is insecure.
To deploy the website professionally, CloudFront is used.

🔹 Why CloudFront?

- Enables full HTTPS (S3 cannot provide HTTPS on custom/static endpoints)

- Global edge locations make the site load faster

- Adds caching, improving performance and reducing S3 costs

- Ensures SEO ranking and browser trust

- Hides the S3 bucket URL for better security

Key CloudFront Settings:

- Origin: S3 Website Endpoint

- Viewer Protocol Policy: Redirect HTTP → HTTPS

- Default Root Object: index.html


### **🛠️ Tech Stack**

Frontend:	              HTML, CSS, JavaScript, React, Vite
Cloud Hosting: 	    Amazon S3
CDN + Security: 	    Amazon CloudFront
Dev Environment:	    VS Code, Node.js, npm


### **📂 Project Structure**
```
TravelHub/
├── dist/
│   ├── index.html
│   ├── assets/
│   └── styles.css
├── public/
│   └── favicon.ico
├── src/
│   ├── components/
│   ├── pages/
│   ├── App.tsx
│   ├── main.tsx
│   └── index.css
├── package.json
├── vite.config.js
└── README.md
```


**🧪 Running the Project Locally**

1️. Clone the Repository
```
git clone https://github.com/your-username/TravelHub.git
```
```
cd TravelHub
```

2. Install Dependencies
```
npm install
```

3️. Start Development Server
```
npm run dev
```

4️. Build for Production
```
npm run build
```

### **🚀 Deploying to AWS S3 + CloudFront**

**Step 1 — Build the Project**
```ts
npm run build
```
**Step 2 — Upload /dist to an S3 Bucket**

**Step 3 — Enable Static Website Hosting**

**Step 4 — Add Public Read Bucket Policy**

**Step 5 — Create a CloudFront Distribution**
- Origin: S3 website endpoint
- Viewer Protocol: Redirect HTTP to HTTPS
- Default Root Object: index.html

**Step 6 — Access Your Website via CloudFront HTTPS URL**


### **📸 Screenshots**


### **🎥 Video Demonstration (YouTube)**
