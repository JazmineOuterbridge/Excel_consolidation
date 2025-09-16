# SharePoint Deployment Guide - Excel File Consolidator

## Quick Start

### Method 1: Upload to Document Library (Recommended)

1. **Access your SharePoint site**
2. **Navigate to a Document Library** (e.g., "Documents", "Site Assets")
3. **Upload the files**:
   - Upload `index.html`
   - Upload `xlsx.full.min.js`
   - Upload `README.md` (optional)
4. **Set permissions** for your users
5. **Access the app** by clicking on `index.html`

### Method 2: Embed in SharePoint Page

1. **Create a new SharePoint page**
2. **Add an "Embed" web part**
3. **Use this code**:
   ```html
   <iframe src="[YOUR_SHAREPOINT_SITE]/[DOCUMENT_LIBRARY]/index.html" 
           width="100%" 
           height="800px" 
           frameborder="0"
           allow="file-upload">
   </iframe>
   ```

### Method 3: Direct Link

1. **Upload files to Document Library**
2. **Create a link web part**
3. **Link to**: `[YOUR_SHAREPOINT_SITE]/[DOCUMENT_LIBRARY]/index.html`
4. **Set to open in new window**

## SharePoint-Specific Considerations

### Security & Permissions

- **User Access**: Ensure users have "Read" permission to the Document Library
- **File Upload**: Users need permission to access the HTML file
- **Cross-Origin**: The app works entirely client-side, no CORS issues

### Browser Compatibility

- **Modern SharePoint**: Works with Edge, Chrome, Firefox
- **Classic SharePoint**: Compatible with Internet Explorer 11+
- **Mobile**: Responsive design works on SharePoint mobile apps

### File Size Limits

- **SharePoint**: No server-side file size limits (all processing is client-side)
- **Browser**: Limited by available browser memory (no artificial limits)
- **Network**: Files never leave the user's device

## Troubleshooting SharePoint Issues

### Common Issues

1. **"File not found" error**:
   - Verify file upload completed successfully
   - Check Document Library permissions
   - Try accessing the file directly via URL

2. **App doesn't load**:
   - Check if SharePoint blocks external CDN resources
   - Verify internet connection for Bootstrap/icon loading
   - Try different browser

3. **Files won't upload in the app**:
   - Check browser file picker permissions
   - Ensure files are .xlsx or .xls format
   - Verify sufficient browser memory for large files

4. **Download doesn't work**:
   - Check browser pop-up blockers
   - Verify download folder permissions
   - Try different browser

### SharePoint Admin Settings

If you're a SharePoint administrator, ensure:

- **Custom Script**: Allow custom scripts if needed
- **CDN Access**: Allow external CDN resources (Bootstrap, icons)
- **File Types**: .html and .js files are allowed
- **Security**: Content Security Policy allows inline scripts

## Testing Checklist

Before deploying to production:

- [ ] Test with different Excel file formats (.xlsx, .xls)
- [ ] Test with files of various sizes (no size limit)
- [ ] Test with multiple files (unlimited)
- [ ] Test download functionality
- [ ] Test on different browsers
- [ ] Test on mobile devices
- [ ] Verify user permissions work correctly

## File Structure for SharePoint

```
Document Library/
├── index.html          (Main application - 27KB)
├── xlsx.full.min.js    (Excel processing library - 882KB)
└── README.md           (Documentation - 6KB)
```

## Support

For SharePoint-specific issues:
1. Check SharePoint admin center settings
2. Verify Document Library permissions
3. Test with different user accounts
4. Check browser console for errors
5. Contact your SharePoint administrator

---

**Note**: This application runs entirely in the browser and never sends data to SharePoint servers. All Excel processing happens client-side for maximum security and privacy.
