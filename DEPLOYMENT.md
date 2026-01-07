# Deployment Guide

This portfolio is now ready to deploy on Render (or any Docker-based platform).

## 🐳 Docker Files Created

- `Dockerfile` - Builds nginx-based container
- `docker-compose.yml` - For local testing with Docker
- `nginx.conf` - Nginx configuration with caching and security headers
- `render.yaml` - Render deployment configuration
- `.dockerignore` - Excludes unnecessary files from Docker build

## 🚀 Deploy to Render

### Method 1: Using Render Dashboard (Recommended)

1. **Push to GitHub:**
   ```bash
   git init
   git add .
   git commit -m "Initial portfolio commit"
   git branch -M main
   git remote add origin <your-github-repo-url>
   git push -u origin main
   ```

2. **Deploy on Render:**
   - Go to [render.com](https://render.com)
   - Click "New +" → "Web Service"
   - Connect your GitHub repository
   - Render will auto-detect the `render.yaml` file
   - Click "Create Web Service"
   - Your site will be live at: `https://azeezat-portfolio.onrender.com` (or custom domain)

### Method 2: Using Render Blueprint (render.yaml)

The `render.yaml` file is already configured. Just push your code to GitHub and Render will automatically:
- Detect the Docker configuration
- Build the container
- Deploy on the free tier
- Provide HTTPS automatically

## 🧪 Test Locally with Docker

If you have Docker installed locally:

```bash
# Build the image
docker build -t azeezat-portfolio .

# Run the container
docker run -p 8080:80 azeezat-portfolio

# Or use docker-compose
docker-compose up
```

Visit `http://localhost:8080` to view your portfolio.

## 🌐 Alternative Deployment Options

### Netlify (Easiest - No Docker needed)
```bash
# Install Netlify CLI
npm install -g netlify-cli

# Deploy
netlify deploy --prod
```

### GitHub Pages (Free - No Docker needed)
1. Push code to GitHub
2. Go to Settings → Pages
3. Select branch → Save
4. Site live at: `https://yourusername.github.io/repository-name`

### Vercel (No Docker needed)
```bash
# Install Vercel CLI
npm install -g vercel

# Deploy
vercel --prod
```

## 📝 What's Configured

### Nginx Configuration
- Gzip compression enabled
- Static asset caching (1 year)
- Security headers (X-Frame-Options, X-Content-Type-Options, X-XSS-Protection)
- SPA routing support

### Render Configuration
- Environment: Docker
- Region: Oregon (change in render.yaml if needed)
- Plan: Free tier
- Health check enabled
- Auto-deploy from GitHub

## 🔧 Customization

### Change Render Region
Edit `render.yaml`:
```yaml
region: oregon  # Options: oregon, frankfurt, singapore, ohio, virginia
```

### Change Port
Edit `nginx.conf` and `render.yaml` if you need a different port.

### Add Environment Variables
Edit `render.yaml`:
```yaml
envVars:
  - key: YOUR_KEY
    value: your_value
```

## 🎯 Next Steps

1. Create a GitHub repository
2. Push this code to GitHub
3. Sign up for Render (free tier)
4. Connect your GitHub repo to Render
5. Deploy automatically!

Your portfolio will be live with:
- ✅ HTTPS enabled
- ✅ Custom domain support
- ✅ Automatic deployments
- ✅ Free hosting

---

**Need help?** Check the [Render documentation](https://render.com/docs) or [contact support](https://render.com/support).
