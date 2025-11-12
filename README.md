# 🌩️ Static Website Hosting on AWS using S3 and CloudFront (HTTPS Enabled)

This project demonstrates how to host a static website using **Amazon S3** and serve it securely through **Amazon CloudFront** using **HTTPS**.  
The setup uses the **AWS Free Tier** and does **not require Route 53 or a custom domain**.

---

## 🧭 Architecture
**User → CloudFront (HTTPS) → S3 (Static Website)**

- **CloudFront:** Provides CDN + SSL/TLS for global content delivery  
- **S3:** Hosts static website files  
- **IAM:** Manages permissions and access control  
- *(Optional)* **ACM:** For custom domain certificates  

📊 **Architecture Diagram**  
![Architecture Diagram](aws-stattic-website/architecture/static-website-architecture.png)

---

## ⚙️ Services Used
**AWS S3** | **AWS CloudFront** | **AWS IAM** | **AWS Certificate Manager (optional)**

---

## 🚀 Deployment Steps

1. **Create an S3 Bucket** and enable **Static Website Hosting**.  
2. **Upload** `index.html`, `style.css`, and any other static files.  
3. **Add a Bucket Policy** to allow public read access.  
4. **Create a CloudFront Distribution** with your **S3 website endpoint** as the origin.  
5. **Enable HTTPS** using the **Default CloudFront certificate**.  
6. Access the website via your **CloudFront domain**, e.g.  https://d123abc.cloudfront.net

---

## 📁 Project Structure

aws-s3-cloudfront-static-website/
├── website/
│ ├── index.html
│ ├── style.css
│ └── images/
├── aws/
│ ├── s3-bucket-policy.json
│ └── cloudfront-setup-notes.md
├── architecture/
│ └── aws-s3-cloudfront-architecture.png
└── README.md


---

## ✅ Verification

- ✅ Visit CloudFront URL → should load your site over **HTTPS**  
- ✅ CloudFront **Status = Deployed**  
- ✅ S3 bucket objects are **Public (Read)**  

---

## 🧰 Tools & Technologies
**AWS S3 | CloudFront | IAM | HTML | CSS | GitHub**

---

## ✨ Author
**Gowri Suresh**  
🔗 [GitHub: Gowri0109](https://github.com/Gowri0109)  
🔗 [LinkedIn: linkedin.com/in/gowrisuresh01](https://linkedin.com/in/gowrisuresh01)

   
