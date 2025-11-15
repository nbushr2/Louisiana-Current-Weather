# 🌐 Hosting Options for Louisiana Weather App

## Two Solutions for Your CMS

You mentioned wanting to either:
1. **Upload GeoJSON separately** (and load externally)
2. **Host HTML in cloud** (and embed via iframe)

**Both work great!** Here's how to do each:

---

## ✅ OPTION 1: External GeoJSON (Recommended for CMS)

### What You Have
- `louisiana_weather_with_alerts_radar.html` (already configured!)
- Your GeoJSON files uploaded to CMS

### Setup Steps

**1. Upload GeoJSON Files to CMS**
```
Location: /_fierce-draft/state-climate-office/_resources/weather-map/

Upload these files:
├── louisiana_state_boundary.geojson
└── louisiana_parishes.geojson
```

**2. Upload HTML File**
```
Upload: louisiana_weather_with_alerts_radar.html
To: Your desired page location
```

**3. Verify Paths**
The HTML already has these paths configured:
```javascript
const GEOJSON_CONFIG = {
    stateBoundary: '/_fierce-draft/state-climate-office/_resources/weather-map/louisiana_state_boundary.geojson',
    parishBoundaries: '/_fierce-draft/state-climate-office/_resources/weather-map/louisiana_parishes.geojson'
};
```

**If your paths are different, just update these lines!**

**4. Test**
- Open the page in CMS preview
- Should load in 2-3 seconds
- Boundaries will appear
- Everything works!

### ✅ Pros of This Method
- Everything in your CMS
- Easy to update/maintain
- No external dependencies
- Fast loading
- Full control

### ⚠️ Cons
- Need CMS access to update
- Slightly slower than embedded
- Requires proper CORS settings (usually automatic)

---

## ✅ OPTION 2: Free Cloud Hosting with iFrame

Perfect for embedding in CMS pages!

### Free Hosting Options

#### **A. GitHub Pages** (Best Choice)
**Features:**
- ✅ 100% Free forever
- ✅ Fast global CDN
- ✅ Custom domain support
- ✅ HTTPS included
- ✅ Easy updates via GitHub

**Setup Steps:**

**1. Create GitHub Account**
- Go to github.com
- Sign up (free)

**2. Create Repository**
```
1. Click "New repository"
2. Name: "louisiana-weather"
3. Check "Public"
4. Check "Add README"
5. Click "Create repository"
```

**3. Upload Files**
```
1. Click "Add file" → "Upload files"
2. Upload:
   - louisiana_weather_with_alerts_radar.html
   - louisiana_state_boundary.geojson
   - louisiana_parishes.geojson
3. Rename HTML to: index.html
4. Click "Commit changes"
```

**4. Enable GitHub Pages**
```
1. Go to Settings
2. Scroll to "Pages"
3. Source: "Deploy from branch"
4. Branch: "main" → "/ (root)"
5. Click "Save"
```

**5. Get Your URL**
```
After 1-2 minutes:
https://YOUR-USERNAME.github.io/louisiana-weather/

Example:
https://lsu-climate.github.io/louisiana-weather/
```

**6. Update GeoJSON Paths in HTML**
```javascript
const GEOJSON_CONFIG = {
    stateBoundary: './louisiana_state_boundary.geojson',
    parishBoundaries: './louisiana_parishes.geojson'
};
```

**7. Embed in CMS**
```html
<iframe 
    src="https://YOUR-USERNAME.github.io/louisiana-weather/" 
    width="100%" 
    height="800px" 
    frameborder="0"
    style="border: none;">
</iframe>
```

---

#### **B. Netlify** (Also Great)
**Features:**
- ✅ Free tier generous
- ✅ Drag-and-drop deployment
- ✅ Auto-deploys from GitHub
- ✅ Custom domain

**Setup Steps:**

**1. Sign Up**
- Go to netlify.com
- Sign up with GitHub

**2. Deploy**
```
1. Click "Add new site" → "Import existing project"
2. Choose GitHub
3. Select your repository
4. Click "Deploy"
```

**3. Get URL**
```
https://YOUR-SITE-NAME.netlify.app
```

**4. Embed**
```html
<iframe 
    src="https://YOUR-SITE-NAME.netlify.app" 
    width="100%" 
    height="800px" 
    frameborder="0">
</iframe>
```

---

#### **C. Cloudflare Pages**
**Features:**
- ✅ Free unlimited requests
- ✅ Fast global CDN
- ✅ GitHub integration

**Setup:** Similar to Netlify

---

#### **D. Vercel**
**Features:**
- ✅ Free hobby tier
- ✅ Fast deployments
- ✅ Great performance

**Setup:** Similar to Netlify

---

### 🎯 Recommendation

**For LSU/University:**
👉 **GitHub Pages**
- Free forever
- Professional
- Easy to maintain
- GitHub = portfolio/resume builder
- Can transfer ownership to LSU organization

**Setup Time:** 10 minutes

---

## 📱 iFrame Embedding Guide

### Basic Embed Code

```html
<iframe 
    src="YOUR-HOSTED-URL"
    width="100%" 
    height="800px"
    frameborder="0"
    style="border: none; display: block;">
</iframe>
```

### Responsive Embed

```html
<div style="position: relative; padding-bottom: 75%; height: 0; overflow: hidden;">
    <iframe 
        src="YOUR-HOSTED-URL"
        style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: none;"
        frameborder="0">
    </iframe>
</div>
```

### Full-Screen Embed

```html
<iframe 
    src="YOUR-HOSTED-URL"
    style="position: fixed; top: 0; left: 0; width: 100vw; height: 100vh; border: none; z-index: 9999;"
    frameborder="0">
</iframe>
```

### In CMS (OmniUpdate)

**1. Create New Page**
```
Content → New Page
Choose template
```

**2. Add Code Block**
```
Insert → Code Block (or HTML component)
```

**3. Paste iframe Code**
```html
<div class="weather-app-container">
    <iframe 
        src="https://YOUR-USERNAME.github.io/louisiana-weather/"
        width="100%" 
        height="800px"
        frameborder="0"
        title="Louisiana Weather"
        style="border: none;">
    </iframe>
</div>
```

**4. Style Container (Optional)**
```html
<style>
.weather-app-container {
    max-width: 1400px;
    margin: 2rem auto;
    box-shadow: 0 4px 20px rgba(0,0,0,0.1);
    border-radius: 12px;
    overflow: hidden;
}
</style>
```

---

## 🔄 Updating Your App

### If Using External GeoJSON (Option 1)
```
1. Edit HTML in CMS
2. Upload new version
3. Clear cache (if needed)
4. Refresh page
```

### If Using GitHub Pages (Option 2)
```
1. Go to your repository
2. Click on index.html
3. Click "Edit" (pencil icon)
4. Make changes
5. Click "Commit changes"
6. Wait 1-2 minutes for deployment
7. Refresh iframe
```

**Pro Tip:** Set up GitHub Desktop app for easier updates!

---

## 📊 Comparison: Option 1 vs Option 2

| Factor | Option 1: External GeoJSON | Option 2: GitHub + iframe |
|--------|---------------------------|--------------------------|
| **Setup Time** | 5 minutes | 10 minutes |
| **Maintenance** | Edit in CMS | Edit in GitHub |
| **Speed** | Fast | Very fast (CDN) |
| **Reliability** | CMS dependent | Independent |
| **Updates** | CMS upload | Git commit |
| **Portability** | CMS only | Use anywhere |
| **Cost** | $0 | $0 |
| **Best For** | Single CMS site | Multiple sites |

---

## 🎯 My Recommendation

### For Your Use Case:

**Start with Option 1** (External GeoJSON in CMS)
- Fastest setup
- Everything in one place
- Easy for your workflow

**Later upgrade to Option 2** (GitHub + iframe) if:
- Want to use on multiple sites
- Want version control
- Want independent hosting
- CMS has issues

---

## 🚀 Quick Start: GitHub Pages Method

### Step-by-Step (10 Minutes)

**1. GitHub Setup (3 min)**
```
☐ Create GitHub account
☐ Create new repository: "louisiana-weather"
☐ Make it public
```

**2. Upload Files (2 min)**
```
☐ Upload index.html (renamed weather app)
☐ Upload louisiana_state_boundary.geojson
☐ Upload louisiana_parishes.geojson
```

**3. Configure (1 min)**
```
☐ Edit index.html
☐ Change GeoJSON paths to:
   './louisiana_state_boundary.geojson'
   './louisiana_parishes.geojson'
☐ Commit changes
```

**4. Enable Pages (1 min)**
```
☐ Settings → Pages
☐ Source: main branch
☐ Save
```

**5. Get URL (1 min)**
```
☐ Copy your URL:
   https://USERNAME.github.io/louisiana-weather/
```

**6. Embed in CMS (2 min)**
```
☐ Create iframe code
☐ Paste in CMS page
☐ Publish
☐ Test
```

**Done!** ✅

---

## 🔧 Troubleshooting

### iFrame Issues

**Issue: iFrame blank/white**
```
Solutions:
- Check URL is correct
- Verify HTTPS (not HTTP)
- Check browser console for errors
- Ensure no content blocking
```

**Issue: CORS errors**
```
Solutions:
- Use relative paths for GeoJSON
- Ensure all files in same origin
- Check GitHub Pages is enabled
```

**Issue: iFrame too small**
```
Solutions:
- Increase height to 800px+
- Use responsive embed code
- Test on different screen sizes
```

### GitHub Pages Issues

**Issue: 404 error**
```
Solutions:
- Wait 2-3 minutes for deployment
- Check file is named index.html
- Verify Pages is enabled
- Check branch is correct
```

**Issue: Changes not showing**
```
Solutions:
- Hard refresh (Ctrl+Shift+R)
- Clear browser cache
- Wait for deployment
- Check commit went through
```

---

## 💡 Pro Tips

### For Best Results:

**1. Use HTTPS**
- Always use https:// in iframe src
- GitHub Pages provides HTTPS automatically

**2. Set Proper Height**
```html
height="800px"  <!-- Good for desktop -->
height="600px"  <!-- Good for mobile -->
```

**3. Add Loading Message**
```html
<iframe src="...">
    Loading weather app...
</iframe>
```

**4. Make Responsive**
```css
iframe {
    width: 100%;
    min-height: 600px;
    height: 80vh;  /* 80% of viewport height */
}
```

**5. Test Thoroughly**
- Test in different browsers
- Test on mobile
- Test in CMS preview
- Test published page

---

## 📋 Checklist: Which Option?

### Choose Option 1 (External GeoJSON) if:
- [ ] You only need it in CMS
- [ ] You prefer simple setup
- [ ] You have CMS admin access
- [ ] You want everything in one place

### Choose Option 2 (GitHub + iframe) if:
- [ ] Want to use on multiple sites
- [ ] Want version control
- [ ] Want independent hosting
- [ ] Want fastest global performance
- [ ] Want to learn GitHub (good skill!)

---

## 🎓 Learning Resources

### GitHub Pages
- Docs: https://pages.github.com/
- Tutorial: https://docs.github.com/en/pages

### iFrames
- MDN Guide: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe
- Best Practices: Search "iframe best practices"

### Git/GitHub
- GitHub Learning Lab: https://lab.github.com/
- Git Tutorial: https://git-scm.com/docs/gittutorial

---

## 📞 Quick Help

### Need Help With Option 1?
```
1. Upload GeoJSON to CMS location
2. Upload weather HTML
3. Verify paths in HTML match CMS
4. Test
```

### Need Help With Option 2?
```
1. Create GitHub repo
2. Upload 3 files
3. Enable Pages
4. Copy URL
5. Create iframe in CMS
```

### Still Stuck?
- Check browser console (F12)
- Verify all files uploaded
- Check file paths
- Test URL directly in browser

---

## ✅ Summary

**Two Great Options:**

**Option 1: External GeoJSON in CMS**
- ✅ Quick setup (5 min)
- ✅ Everything in CMS
- ✅ Easy maintenance
- 👉 **Best for single-site use**

**Option 2: GitHub Pages + iFrame**
- ✅ Free forever
- ✅ Fast global CDN
- ✅ Version control
- ✅ Use anywhere
- 👉 **Best for multi-site use**

**Both work perfectly!** Choose based on your needs.

---

## 🎉 Ready to Deploy?

**Option 1 Users:**
1. Upload GeoJSON files to CMS ✓
2. Upload weather HTML ✓
3. Test ✓
4. Done! 🎉

**Option 2 Users:**
1. Create GitHub repo ✓
2. Upload files ✓
3. Enable Pages ✓
4. Embed iframe ✓
5. Done! 🎉

**Need help deciding?** Option 1 is simpler for CMS-only use!

---

**Created**: November 15, 2025  
**Updated**: With both hosting options  
**Status**: Ready to deploy  
**Support**: Both methods fully documented
