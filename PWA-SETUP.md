# 🎓 Orad Academic Dash - PWA Setup Guide

## Overview
This is a fully mobile-optimized Progressive Web App (PWA) for tracking academic progress, designed specifically for Android devices like the Samsung S24 Ultra.

## Features ✨
- 📱 Mobile-first responsive design
- 🔄 Offline support with Service Worker
- 💾 LocalStorage persistence
- 🎯 Customizable degree credit requirements
- 📊 Grade tracking with weighted components
- ⏰ Deadline management
- 🎨 Modern, thumb-friendly UI
- 📲 Installable as a native app on Android

## Files in This Project

```
📁 ClaudeProjects/
├── StudentDashboard.html    # Main PWA application
├── manifest.json            # PWA manifest configuration
├── service-worker.js        # Offline caching & PWA functionality
├── generate-icons.html      # Icon generator tool
├── PWA-SETUP.md            # This file
└── icon-*.png              # App icons (generate these!)
```

## Quick Start

### Step 1: Generate Icons
1. Open `generate-icons.html` in your browser
2. Click "Generate All Icons"
3. Save all downloaded icons to the project folder
4. Icons will be named: `icon-72x72.png`, `icon-96x96.png`, etc.

### Step 2: Test Locally

#### Option A: Using Python
```bash
# Navigate to project folder
cd C:\Users\אורעד\ClaudeProjects

# Start a local server (Python 3)
python -m http.server 8000

# Or Python 2
python -m SimpleHTTPServer 8000
```

#### Option B: Using Node.js
```bash
# Install http-server globally
npm install -g http-server

# Navigate to project folder
cd C:\Users\אורעד\ClaudeProjects

# Start server
http-server -p 8000
```

#### Option C: Using VS Code
1. Install "Live Server" extension
2. Right-click `StudentDashboard.html`
3. Select "Open with Live Server"

### Step 3: Access on Desktop
Open browser and go to:
```
http://localhost:8000/StudentDashboard.html
```

## Installing on Android (S24 Ultra)

### Method 1: Via Chrome Browser
1. **Ensure HTTPS** (required for PWA installation):
   - Use a service like [ngrok](https://ngrok.com/) to create HTTPS tunnel
   - Or deploy to GitHub Pages / Netlify / Vercel

2. **On your S24 Ultra:**
   - Open Chrome browser
   - Navigate to your app URL
   - Tap the menu (⋮) → "Install app" or "Add to Home screen"
   - App icon will appear on your home screen

### Method 2: Via USB Debugging (for local testing)
1. **On your PC:**
   ```bash
   adb reverse tcp:8000 tcp:8000
   ```

2. **On S24 Ultra:**
   - Open Chrome
   - Go to `http://localhost:8000/StudentDashboard.html`
   - Install via menu

### Method 3: Deploy to Production (Recommended)

#### GitHub Pages (Free)
1. Create a GitHub repository
2. Upload all project files
3. Go to Settings → Pages
4. Select main branch
5. Your app will be at: `https://yourusername.github.io/repo-name/StudentDashboard.html`

#### Netlify (Free, Easiest)
1. Drag and drop project folder to [Netlify Drop](https://app.netlify.com/drop)
2. Get instant HTTPS URL
3. Access from any device

## PWA Features Explanation

### Offline Support
The service worker caches the app for offline use. After the first visit, the app works without internet.

### Settings (⚙️ button)
- **Total Degree Credits**: Customize your degree requirements (default: 120)
- Settings persist in localStorage

### Data Persistence
All data (courses, deadlines, settings) is saved to localStorage automatically:
- Courses with grades
- Deadlines
- Custom credit requirements

### Mobile Optimizations
- **Touch targets**: Minimum 48px for easy thumb navigation
- **Bottom sheets**: Modals slide up from bottom on mobile
- **Responsive grids**: 2-column on mobile, 4-column on tablet+
- **High DPI ready**: Optimized for S24 Ultra's 501 PPI display
- **Safe areas**: Respects notch/camera cutouts
- **No zoom issues**: Proper viewport configuration

## Customization

### Change Theme Colors
Edit the CSS variables in `StudentDashboard.html`:
```css
:root {
    --primary-color: #667eea;     /* Change this */
    --secondary-color: #764ba2;   /* And this */
    --primary-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}
```

### Modify Icon
Edit the `drawIcon()` function in `generate-icons.html`, then regenerate icons.

### App Name
Change in `manifest.json`:
```json
{
  "name": "Your Custom Name",
  "short_name": "Custom Name"
}
```

## Browser Support

### Recommended
- ✅ Chrome/Edge (Android) - Full PWA support
- ✅ Samsung Internet - Full PWA support

### Limited Support
- ⚠️ Firefox (Android) - Works, but no install prompt
- ⚠️ Safari (iOS) - Works, but limited PWA features

## Troubleshooting

### "Install App" option not showing
- Ensure you're using HTTPS (not HTTP)
- Check that `manifest.json` is linked correctly
- Service worker must register successfully
- Icons must exist and be accessible

### Icons not loading
- Verify all icon files are in the same folder
- Check browser console for 404 errors
- Regenerate icons using `generate-icons.html`

### Data not persisting
- Check localStorage is enabled in browser
- Don't use incognito/private mode
- Check browser console for errors

### Service Worker issues
```javascript
// Check registration in browser console:
navigator.serviceWorker.getRegistrations().then(console.log)

// Unregister if needed:
navigator.serviceWorker.getRegistrations().then(reg => reg[0].unregister())
```

## Performance Tips

### S24 Ultra Specific
- App is optimized for 1440 x 3088 resolution
- High-DPI icons (512x512) prevent blurriness
- Hardware-accelerated animations
- Proper viewport for edge-to-edge display

### Best Practices
- Clear old service worker cache periodically
- Limit localStorage to < 5MB
- Export data regularly (future feature idea!)

## Future Enhancements Ideas

- 📤 Export/Import data (JSON/CSV)
- 📈 Charts and visualizations
- 🔔 Push notifications for deadlines
- 🌙 Dark mode toggle
- ☁️ Cloud sync (Firebase/Supabase)
- 📊 Semester GPA comparisons
- 🏆 Achievement badges

## Support

For issues or questions:
1. Check browser console for errors
2. Verify all files are in correct location
3. Test on desktop first, then mobile
4. Ensure HTTPS for full PWA features

## Credits

Built for Orad's academic tracking needs.
Designed with mobile-first principles and PWA best practices.

---

**Last Updated**: February 2026
**Version**: 1.0.0
**Optimized For**: Android (S24 Ultra, high-res screens)
