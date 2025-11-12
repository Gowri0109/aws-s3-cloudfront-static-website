# ☁️ CloudFront Setup Notes

These notes summarize how **Amazon CloudFront** was configured to securely deliver the static website hosted on **Amazon S3** using HTTPS.  
The setup uses only **S3** and **CloudFront** (no Route 53 or custom domain).

---

## 🔧 CloudFront Configuration Summary

| Setting | Value / Description |
|----------|--------------------|
| **Origin Domain Name** | `your-bucket-name.s3-website.<region>.amazonaws.com` *(S3 website endpoint)* |
| **Origin Protocol Policy** | HTTP Only *(S3 website endpoints only support HTTP)* |
| **Viewer Protocol Policy** | Redirect HTTP to HTTPS |
| **Allowed HTTP Methods** | GET, HEAD |
| **Cache Policy** | CachingOptimized (default) |
| **Default Root Object** | `index.html` |
| **SSL Certificate** | Default CloudFront certificate (*.cloudfront.net) |
| **Price Class** | Use only North America, Europe, Asia, Middle East, Africa |
| **WAF (Web Application Firewall)** | Not enabled *(optional, extra cost)* |
| **Logging** | Disabled *(can be enabled for monitoring later)* |

---

## 🚀 Deployment Steps

1. Open **CloudFront Console** → **Create Distribution**
2. Select **Origin Domain** → choose your **S3 Website Endpoint**
3. Set **Origin Protocol Policy** → `HTTP Only`
4. Under **Default Cache Behavior:**
   - Viewer Protocol Policy → `Redirect HTTP to HTTPS`
   - Allowed Methods → `GET, HEAD`
   - Compress objects automatically → ✅ Enabled
5. Under **Settings:**
   - Default Root Object → `index.html`
   - SSL Certificate → Default CloudFront Certificate
   - Price Class → Use only “North America, Europe, Asia, Middle East, Africa”
6. Click **Create Distribution**
7. Wait for **Status = Deployed** (may take 10–15 minutes)

---

## 🔒 Verification

After deployment:
- Access the CloudFront domain, e.g.  https://dXXXXXXXXXXXX.cloudfront.net

- Ensure the page loads using **HTTPS**.  
- Confirm the green lock icon 🔒 in your browser.  
- Status should be **Deployed** in the CloudFront console.

---

## ⚠️ Troubleshooting Tips

| Issue | Likely Cause | Fix |
|-------|---------------|-----|
| **403 Forbidden** | Bucket policy missing or objects not public | Add correct public read bucket policy |
| **504 Gateway Timeout** | CloudFront origin misconfigured | Use *S3 website endpoint* + set Origin Protocol Policy = HTTP Only |
| **404 Not Found** | `index.html` missing in bucket root | Upload index.html and set Default Root Object |
| **HTTPS not working** | Using wrong SSL cert or domain | Use default CloudFront certificate |
| **Slow updates** | Cached content | Invalidate cache → CloudFront → Invalidations → `/*` |

---

## 🧾 Cleanup (to avoid charges)
1. **Disable** CloudFront distribution.  
2. Wait until status = *Disabled*.  
3. **Delete** the distribution.  
4. Then delete the S3 bucket.

---

## 👩‍💻 Author
**Gowri Suresh**  
🔗 [GitHub: Gowri0109](https://github.com/Gowri0109)  
🔗 [LinkedIn: linkedin.com/in/gowrisuresh01](https://linkedin.com/in/gowrisuresh01)

