# Excel File Consolidator - SharePoint Deployment Guide

## Overview
This is a complete, self-contained web application that allows users to upload multiple Excel files (.xlsx/.xls) and consolidate them into a single workbook with separate sheets. The application runs entirely in the browser with no server-side processing required.

## Features
- **Drag & Drop Upload**: Intuitive file upload with visual feedback
- **File Validation**: Supports .xlsx and .xls files up to 5MB each (max 10 files)
- **Excel Processing**: Uses SheetJS library for robust Excel file handling
- **Consolidation**: Creates new workbook with each uploaded file as a separate sheet
- **Client-Side Only**: No data leaves the user's browser
- **Responsive Design**: Works on desktop and mobile devices
- **Accessibility**: ARIA labels and keyboard navigation support
- **Error Handling**: Comprehensive validation and user-friendly error messages

## SharePoint Deployment Instructions

### Method 1: Upload to Document Library (Recommended)

1. **Access SharePoint Site**:
   - Navigate to your SharePoint site
   - Go to the Document Library where you want to host the app

2. **Upload the File**:
   - Click "Upload" → "Files"
   - Select the `index.html` file
   - Ensure it uploads successfully

3. **Set Permissions**:
   - Right-click the uploaded file
   - Select "Manage access" or "Share"
   - Set appropriate permissions for your users

4. **Access the Application**:
   - Click on the uploaded `index.html` file
   - It will open in a new browser tab
   - The application will be fully functional

### Method 2: Embed in SharePoint Page

1. **Create a New Page**:
   - In SharePoint, go to "Pages" in the left navigation
   - Click "New" → "Page"
   - Choose a template or start with a blank page

2. **Add Web Part**:
   - Click the "+" icon to add a web part
   - Select "Embed" or "Script Editor" web part
   - If using Embed, you'll need to host the file elsewhere first

3. **Alternative - Direct Link**:
   - Create a link web part
   - Link to the `index.html` file URL from your document library
   - Set it to open in a new window/tab

### Method 3: SharePoint Framework (SPFx) Extension

For advanced integration:

1. **Create SPFx Extension**:
   ```bash
   yo @microsoft/sharepoint
   # Select "Extension" → "Application Customizer"
   ```

2. **Embed the HTML**:
   - Copy the HTML content into your extension
   - Deploy as a SharePoint Framework solution

### Method 4: Modern Page with iframe

1. **Create Modern Page**:
   - Go to "Pages" → "New" → "Page"
   - Add a "Text" web part

2. **Add iframe Code**:
   ```html
   <iframe src="[YOUR_SHAREPOINT_SITE]/[DOCUMENT_LIBRARY]/index.html" 
           width="100%" 
           height="800px" 
           frameborder="0">
   </iframe>
   ```

## Configuration Options

### Customizing File Limits
Edit the following constants in the JavaScript section:
```javascript
this.maxFiles = 10;        // Maximum number of files
this.maxFileSize = 5 * 1024 * 1024; // 5MB per file
```

### Styling Customization
The application uses Bootstrap 5 for styling. You can:
- Modify the CSS variables in the `<style>` section
- Change color schemes by updating the Bootstrap classes
- Adjust the gradient in the header section

### Sheet Naming Convention
The application automatically generates sheet names based on filenames. To modify this behavior, edit the `generateSheetName()` method.

## Security Considerations

- **Client-Side Only**: All processing happens in the browser
- **No Data Transmission**: Files never leave the user's device
- **File Validation**: Strict validation prevents malicious file uploads
- **CDN Dependencies**: Uses trusted CDNs for Bootstrap and SheetJS

## Browser Compatibility

- **Chrome**: 60+ (Recommended)
- **Firefox**: 55+
- **Safari**: 12+
- **Edge**: 79+
- **Internet Explorer**: Not supported (uses ES6+ features)

## Troubleshooting

### Common Issues

1. **Files Not Uploading**:
   - Check file size (must be < 5MB)
   - Verify file format (.xlsx or .xls only)
   - Ensure browser supports FileReader API

2. **Processing Errors**:
   - Verify SheetJS library loaded correctly
   - Check browser console for JavaScript errors
   - Ensure files are not corrupted

3. **Download Not Working**:
   - Check if browser blocks pop-ups
   - Verify sufficient disk space
   - Try different browser if issues persist

### SharePoint-Specific Issues

1. **File Access Denied**:
   - Check SharePoint permissions
   - Ensure user has "Read" access to the document library

2. **Page Not Loading**:
   - Verify the file uploaded correctly
   - Check SharePoint site settings for custom scripts
   - Try accessing the file directly via URL

3. **iframe Issues**:
   - Some SharePoint configurations block iframe embedding
   - Use direct file access instead of iframe

## Testing

### Test Scenarios

1. **File Upload**:
   - Drag and drop multiple Excel files
   - Use file picker to select files
   - Try uploading invalid file types

2. **File Processing**:
   - Upload files with multiple sheets
   - Upload large files (near 5MB limit)
   - Upload maximum number of files (10)

3. **Consolidation**:
   - Process files with different formats
   - Verify sheet names are generated correctly
   - Check that data and formatting are preserved

4. **Download**:
   - Verify downloaded file opens correctly
   - Check that all sheets are present
   - Confirm data integrity

### Sample Test Files

Create these test files for comprehensive testing:
- `test1.xlsx` - Simple data in Sheet1
- `test2.xlsx` - Multiple sheets with formulas
- `test3.xls` - Legacy format file
- `large_file.xlsx` - File near 5MB limit

## Support

For issues specific to this application:
1. Check the browser console for error messages
2. Verify all CDN resources are loading correctly
3. Test with different browsers
4. Ensure SharePoint permissions are correct

For SharePoint-specific issues, consult your SharePoint administrator or Microsoft documentation.

## Version Information

- **Application Version**: 1.0.0
- **Bootstrap Version**: 5.3.0
- **SheetJS Version**: 0.20.0
- **Last Updated**: 2024

---

*This application is designed to be completely self-contained and requires no server-side components. All processing is performed client-side for maximum security and privacy.*
