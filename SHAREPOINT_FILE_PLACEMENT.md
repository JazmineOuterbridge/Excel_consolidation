# SharePoint File Placement Guide

## Problem: CDN Fallback Not Working

When the CDN fallback fails, you need to ensure the `xlsx.full.min.js` file is properly placed in SharePoint so the application can find it.

## Solution: Use the SharePoint-Optimized Version

### Option 1: Use the New SharePoint-Optimized File (Recommended)

1. **Replace your current `index.html`** with `index_sharepoint.html`
2. **Upload both files to the same SharePoint folder**:
   ```
   Your SharePoint Document Library/
   ├── index_sharepoint.html    (rename this to index.html)
   └── xlsx.full.min.js
   ```

### Option 2: Fix the Original File

If you want to keep using the original `index.html`, here are the correct SharePoint deployment methods:

## SharePoint Deployment Methods

### Method 1: Same Directory (Recommended)

**File Structure:**
```
Document Library/
├── index.html
└── xlsx.full.min.js
```

**Steps:**
1. Upload both files to the same Document Library folder
2. Access via: `https://yoursite.sharepoint.com/sites/yoursite/Shared%20Documents/index.html`

### Method 2: Subfolder Structure

**File Structure:**
```
Document Library/
├── ExcelApp/
│   ├── index.html
│   └── xlsx.full.min.js
```

**Steps:**
1. Create a subfolder called "ExcelApp"
2. Upload both files to this subfolder
3. Access via: `https://yoursite.sharepoint.com/sites/yoursite/Shared%20Documents/ExcelApp/index.html`

### Method 3: Site Assets Library

**File Structure:**
```
Site Assets/
├── index.html
└── xlsx.full.min.js
```

**Steps:**
1. Go to Site Contents → Site Assets
2. Upload both files to Site Assets
3. Access via: `https://yoursite.sharepoint.com/sites/yoursite/SiteAssets/index.html`

## Troubleshooting File Path Issues

### Check Current URL Structure

1. **Open your SharePoint site**
2. **Navigate to the Document Library**
3. **Right-click on `index.html`** → "Copy link"
4. **Check the URL structure**

**Example URLs:**
- `https://company.sharepoint.com/sites/team/Shared%20Documents/index.html`
- `https://company.sharepoint.com/sites/team/Shared%20Documents/ExcelApp/index.html`

### Verify File Placement

1. **Ensure both files are in the same folder**
2. **Check file permissions** (both files need "Read" access)
3. **Verify file names** (case-sensitive)

### Test the Connection

1. **Open browser developer tools** (F12)
2. **Go to Console tab**
3. **Load your SharePoint page**
4. **Look for these messages**:
   - ✅ `"SheetJS loaded from: ./xlsx.full.min.js"`
   - ❌ `"Failed to load from: ./xlsx.full.min.js"`

## Alternative Solutions

### If CDN is Blocked

Some SharePoint environments block external CDNs. In this case:

1. **Use the SharePoint-optimized version** (`index_sharepoint.html`)
2. **Ensure `xlsx.full.min.js` is uploaded locally**
3. **The app will try multiple paths automatically**

### If File Paths Don't Work

1. **Use absolute URLs** instead of relative paths
2. **Update the script source** in the HTML file:
   ```html
   <script src="https://yoursite.sharepoint.com/sites/yoursite/Shared%20Documents/xlsx.full.min.js"></script>
   ```

## Quick Fix Commands

### For SharePoint Online

1. **Upload files to same directory**
2. **Rename `index_sharepoint.html` to `index.html`**
3. **Test the application**

### For On-Premises SharePoint

1. **Place files in same folder**
2. **Check IIS permissions**
3. **Verify MIME types** (.js files should be allowed)

## Testing Checklist

- [ ] Both files uploaded to SharePoint
- [ ] Files in same directory/folder
- [ ] Proper permissions set
- [ ] Browser console shows successful loading
- [ ] Application loads without errors
- [ ] File upload functionality works

## Need Help?

If you're still having issues:

1. **Check browser console** for specific error messages
2. **Verify SharePoint permissions**
3. **Try the SharePoint-optimized version**
4. **Contact your SharePoint administrator**

---

**Remember**: The key is ensuring both `index.html` and `xlsx.full.min.js` are in the same SharePoint folder with proper permissions!
