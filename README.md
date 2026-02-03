# ASIS Boats Quotation System v28

A professional quotation generator for ASIS Boats salesmen.

## Features

- **6-Page Professional PDF Generation:**
  1. Cover Page (dynamic)
  2. Company Presentation (static)
  3. Quotation Details (dynamic)
  4. Accessory Annex (dynamic, multi-page)
  5. Technical Specifications (boat-specific)
  6. Terms & Conditions (static)

- Multi-currency support (USD, AED, EUR)
- Dynamic pricing calculations
- Boat configuration (GRP, Aluminum, HDIB)
- Accessory selection with category grouping

## Folder Structure

```
asis-quotation-system/
├── index.html              # Main application
├── assets/
│   ├── pdf/
│   │   ├── company_presentation.pdf   # Page 2 - static
│   │   └── terms_conditions.pdf       # Page 6 - static
│   └── images/
│       ├── arrow.png       # Cover page decoration
│       ├── shield.png      # ASIS shield logo
│       └── stamp.png       # Quality stamp
└── specs/                  # Technical specification PDFs
    ├── grp_4_1.pdf        # GRP 4.1M specs
    ├── grp_5_1.pdf        # GRP 5.1M specs
    ├── grp_5_5.pdf        # GRP 5.5M specs
    ├── grp_6_5.pdf        # GRP 6.5M specs
    ├── grp_7_2.pdf        # GRP 7.2M specs
    ├── grp_8_0.pdf        # GRP 8.0M specs
    ├── grp_9_5.pdf        # GRP 9.5M specs
    ├── grp_12.pdf         # GRP 12M specs
    ├── alu_6_5.pdf        # Aluminum 6.5M specs
    ├── alu_7_6.pdf        # Aluminum 7.6M specs
    ├── alu_8_5.pdf        # Aluminum 8.5M specs
    ├── alu_9_5.pdf        # Aluminum 9.5M specs
    ├── alu_11_5.pdf       # Aluminum 11.5M specs
    └── alu_13.pdf         # Aluminum 13M specs
```

## Deployment to Vercel

1. **Push to GitHub:**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/YOUR_USERNAME/asis-quotation-system.git
   git push -u origin main
   ```

2. **Deploy on Vercel:**
   - Go to [vercel.com](https://vercel.com)
   - Import your GitHub repository
   - Deploy (no build configuration needed)

3. **Update Base URL (if needed):**
   In `index.html`, find the `PDF_CONFIG` object and update the `baseUrl`:
   ```javascript
   const PDF_CONFIG = {
       baseUrl: 'https://your-app.vercel.app', // Update this
       // ...
   };
   ```

## Adding New Spec Sheets

### Naming Convention:
- **GRP boats:** `grp_X_X.pdf` (e.g., `grp_7_2.pdf` for 7.2M)
- **Aluminum boats:** `alu_X_X.pdf` (e.g., `alu_8_5.pdf` for 8.5M)
- **HDIB boats:** `hdib_X_X.pdf` (future - not yet implemented)

### To Add:
1. Name the PDF following the convention above
2. Place it in the `/specs/` folder
3. Commit and push to GitHub
4. Vercel will auto-deploy

## Local Testing

To test locally, use a simple HTTP server:

```bash
# Using Python
python -m http.server 8000

# Using Node.js
npx serve
```

Then open `http://localhost:8000` in your browser.

## PDF Configuration

The PDF generation is controlled by the `PDF_CONFIG` object in `index.html`:

```javascript
const PDF_CONFIG = {
    baseUrl: '',  // Set to your Vercel URL for production
    
    staticPdfs: {
        companyPresentation: '/assets/pdf/company_presentation.pdf',
        termsConditions: '/assets/pdf/terms_conditions.pdf'
    },
    
    specsFolder: '/specs/',
    
    images: {
        asusLogo: '/assets/images/asis_logo.png',
        shield: '/assets/images/shield.png',
        arrow: '/assets/images/arrow.png',
        stamp: '/assets/images/stamp.png',
        diamondLogo: '/assets/images/diamond_logo.png'
    }
};
```

## Future Updates

When you update the UI and need to update PDF generation:

1. Tell me: **"Field X changed ID from Y to Z"**
2. Or: **"Added new field X"** (and where it should appear in PDF)
3. Or: **"Removed field X"**
4. Upload the new HTML version

## Technical Notes

- Uses **pdf-lib** library for PDF generation and merging
- Static PDFs are embedded into the final document
- Dynamic pages are generated programmatically
- Supports multi-page annex if many accessories selected
- Falls back to simplified PDF if static assets are unavailable

## Version History

- **v28:** Complete 6-page PDF generation system
- **v27:** Added boat quantity field
- **v11-v26:** UI refinements and accessory updates
