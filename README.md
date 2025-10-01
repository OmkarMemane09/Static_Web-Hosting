# Static_Web-Hosting
Static website hosted on AWS S3 using bucket configuration for global access.

# 🌐 Deploying a Static Website on AWS S3

Amazon S3 (Simple Storage Service) provides a **serverless, cost-effective solution** for hosting static websites.  
It supports **HTML, CSS, JavaScript, images, and other static files** without requiring a web server.  

By enabling **Static Website Hosting** in S3 and configuring permissions, you can deploy your website with a public URL.  
Optionally, you can integrate it with **Route 53 (DNS)** and **CloudFront (CDN)** for a custom domain and faster delivery.  

---

## 🚀 Steps to Deploy

### **Step 1: Create a Bucket**
- Navigate to the **S3 service** in the AWS Management Console.
- Click on **Create bucket**.
- Configure:
  - ✅ **Bucket Name**: Must be globally unique (e.g., `my-website-demo`).
  - ✅ **Region**: Choose one close to your target audience for faster access.
  - ✅ **Object Ownership**: Recommended → *Bucket owner preferred*.
- Leave other settings as default → Click **Create bucket**.

> 📌 Buckets are containers in S3 where all your files will be stored.  
> The bucket name will form part of your website’s endpoint URL.

---

### **Step 2: Upload Website Files**
- Open the newly created bucket.
- Click **Upload → Add files**.
- Select and upload your website’s static files:
  - `index.html` (homepage)
  - `style.css` (styles)
  - `script.js` (JavaScript)
  - Any images or assets used.
- ⚠️ Do not upload the entire folder — only upload files (or structured folders with assets).

> 📌 `index.html` is mandatory because it serves as the default homepage for your static website.

---

### **Step 3: Enable Static Website Hosting**
- Go to the **Properties** tab of your bucket.
- Scroll to **Static website hosting** → Click **Edit**.
- Enable **Static website hosting**.
- Provide:
  - **Index document** → `index.html`
  - *(Optional)* **Error document** → `error.html` (for handling 404 errors)
- Save changes.

> 📌 This step generates a **bucket endpoint URL** (e.g., `http://my-website-demo.s3-website-ap-south-1.amazonaws.com/`) that users can use to access your site.

---

### **Step 4: Configure Permissions**
By default, S3 buckets are **private**. To host a public website, permissions must be updated:

1. **Disable Block Public Access**
   - Go to **Permissions → Block public access (bucket settings)**.
   - 🔓 Uncheck **Block all public access**.
   - Confirm the warning.

2. **Set Object Ownership**
   - Ensure **ACLs enabled**.
   - Choose **Bucket owner preferred**.

3. **Access Control List (ACL)**
   - Under **Access Control List**, for **Everyone (public access)**:
     - ✅ Allow **Read** (for objects/files).
     - ✅ Allow **List** (to view files).

> ⚠️ Be cautious when granting public access. Only enable it if you intend to host public content.

---

### **Step 5: Make Objects Public**
- Navigate to the **Objects** tab.
- Select all uploaded files.
- Choose **Actions → Make public using ACL**.
- Confirm.

> 📌 This ensures that users can directly access your files via the public endpoint.

---

### **Step 6: Access the Website**
- Go to **Properties → Static website hosting**.
- Copy the **Bucket website endpoint URL**.
- Open the URL in your browser to view the hosted static website.

Example:  http://host-demo-web.s3-website.eu-north-1.amazonaws.com


## Website Look Like 
<img width="1898" height="981" alt="image" src="https://github.com/user-attachments/assets/cf8961d4-5fee-4e59-befb-58616f50652a" />
