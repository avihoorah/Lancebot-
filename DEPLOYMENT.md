# 🚀 Deployment Guide

## GitHub Pages (Recommended)

### Initial Setup

1. **Create GitHub Repository**
   ```bash
   # If you haven't initialized git yet
   git init
   git add .
   git commit -m "Initial commit: Lancebot demo"
   ```

2. **Push to GitHub**
   ```bash
   # Create a new repository on github.com, then:
   git remote add origin https://github.com/yourusername/lancebot-demo.git
   git branch -M main
   git push -u origin main
   ```

3. **Enable GitHub Pages**
   - Go to repository **Settings**
   - Click **Pages** in the sidebar
   - Under **Source**, select `main` branch
   - Click **Save**
   - Your site will be live at: `https://yourusername.github.io/lancebot-demo`

### Custom Domain (Optional)

1. Add a `CNAME` file with your domain:
   ```bash
   echo "lancebot.yourdomain.com" > CNAME
   git add CNAME
   git commit -m "Add custom domain"
   git push
   ```

2. Configure DNS with your provider:
   - Add a `CNAME` record pointing to `yourusername.github.io`
   - Wait for DNS propagation (up to 24 hours)

---

## Alternative Hosting Options

### Netlify

1. **Connect Repository**
   - Go to [netlify.com](https://netlify.com)
   - Click "New site from Git"
   - Choose GitHub and select your repository

2. **Configure Build**
   - Build command: (leave empty)
   - Publish directory: `/`

3. **Deploy**
   - Click "Deploy site"
   - Your site will be live at: `random-name.netlify.app`

### Vercel

1. **Import Project**
   - Go to [vercel.com](https://vercel.com)
   - Click "New Project"
   - Import your GitHub repository

2. **Deploy**
   - Click "Deploy"
   - Your site will be live at: `lancebot-demo.vercel.app`

### Static Hosting (Manual)

Upload these files to any static host:
```
├── index.html
├── assets/
│   ├── images/
│   └── products/
```

Supported hosts:
- AWS S3 + CloudFront
- Google Cloud Storage
- Azure Static Web Apps
- Cloudflare Pages

---

## 🔧 Build Optimization

### Image Optimization

```bash
# Install imagemin (optional)
npm install -g imagemin-cli imagemin-webp

# Convert PNGs to WebP
imagemin assets/products/*.png --out-dir=assets/products --plugin=webp
```

### HTML Minification

```bash
# Install html-minifier
npm install -g html-minifier

# Minify index.html
html-minifier --collapse-whitespace --remove-comments \
  --minify-css true --minify-js true \
  index.html -o index.min.html
```

---

## 📊 Analytics (Optional)

### Google Analytics

Add before closing `</head>` in `index.html`:

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

### Plausible (Privacy-friendly)

```html
<script defer data-domain="yourdomain.com" src="https://plausible.io/js/script.js"></script>
```

---

## ✅ Pre-Deployment Checklist

- [ ] Test on multiple browsers (Chrome, Firefox, Safari)
- [ ] Test on mobile devices (iOS, Android)
- [ ] Verify all images load correctly
- [ ] Check all links work
- [ ] Test keyboard shortcuts
- [ ] Verify responsive design at different breakpoints
- [ ] Test sharing functionality
- [ ] Check console for errors
- [ ] Validate HTML (https://validator.w3.org/)
- [ ] Test performance (https://pagespeed.web.dev/)
- [ ] Update README with live demo URL

---

## 🔄 Continuous Deployment

Every push to `main` branch automatically deploys to:
- ✅ GitHub Pages
- ✅ Netlify
- ✅ Vercel

No build process needed - it's pure HTML/CSS/JS!

---

## 🆘 Troubleshooting

### Images not loading
- Check file paths are correct
- Verify case-sensitivity (use lowercase)
- Ensure images are in `assets/` folder

### GitHub Pages 404
- Make sure `index.html` is in root directory
- Check Pages is enabled in repository settings
- Wait 5-10 minutes after enabling

### Custom domain not working
- Verify DNS records are correct
- Check CNAME file is in root directory
- Allow 24 hours for DNS propagation

---

**Need help?** Open an issue on GitHub!
