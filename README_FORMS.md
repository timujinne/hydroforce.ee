# Hydraulic Cylinder Forms - Complete Package

## 📦 Package Contents

This package contains complete forms for hydraulic cylinder specification requests in **Russian** and **English**.

---

## 📄 Files Included

### HTML Forms (Front-end)
| File | Language | Description |
|------|----------|-------------|
| `Form_hc.html` | 🇷🇺 Russian | Complete standalone form (Russian version) |
| `Form_hc_en.html` | 🇬🇧 English | Complete standalone form (English version) |

### WordPress Handlers (Back-end)
| File | Language | Description |
|------|----------|-------------|
| `functions-hydraulic-form.php` | 🇷🇺 Russian | WordPress integration for Russian form |
| `functions-hydraulic-form-en.php` | 🇬🇧 English | WordPress integration for English form |

### Documentation
| File | Language | Description |
|------|----------|-------------|
| `INSTALLATION_INSTRUCTIONS.md` | 🇬🇧 English | Detailed installation guide |
| `ИНСТРУКЦИЯ.md` | 🇷🇺 Russian | Quick start guide (Russian) |
| `README_FORMS.md` | 🇬🇧 English | This file - overview |

---

## ✨ Features

### Form Functionality
- ✅ **Multi-step specification form** with 8 sections
- ✅ **Dynamic conditional fields** (show/hide based on selections)
- ✅ **Client-side validation** for required fields
- ✅ **Loading animations** during submission
- ✅ **Success/Error messages** with auto-scroll
- ✅ **Responsive design** (works on mobile, tablet, desktop)
- ✅ **Professional styling** matching Hydroforce brand

### WordPress Integration
- ✅ **Custom Post Type** for storing requests
- ✅ **Admin panel interface** with custom columns
- ✅ **Automatic email notifications** to admin
- ✅ **Client confirmation emails** with branding
- ✅ **AJAX submission** (no page reload)
- ✅ **Security** with nonce verification
- ✅ **Data validation** on server side

### Email Notifications
- ✅ **HTML formatted emails** with professional styling
- ✅ **Admin notification** with full request details
- ✅ **Client confirmation** with company branding
- ✅ **Direct links** to admin panel from email
- ✅ **Reply-To** set to client email for easy response

---

## 🚀 Quick Start

### For WordPress Sites:

1. **Add PHP handler to theme:**
   ```php
   // In functions.php
   require_once get_template_directory() . '/functions-hydraulic-form-en.php';
   ```

2. **Create WordPress page:**
   - Copy HTML body content from `Form_hc_en.html`
   - Paste into new page
   - Publish

3. **Add CSS:**
   - Copy styles from `Form_hc_en.html`
   - Add to theme stylesheet

4. **Test the form!**

**Detailed instructions:** See `INSTALLATION_INSTRUCTIONS.md`

---

### For Standalone HTML (No WordPress):

1. **Upload `Form_hc_en.html` to your server**
2. **Open in browser** - it will work in "Demo Mode"
3. **Note:** No emails will be sent in demo mode

To enable email sending without WordPress, you'll need a custom PHP email handler.

---

## 📋 Form Sections

The form collects detailed specifications across 8 sections:

1. **Contact Information** - Company, person, email, phone
2. **General Information** - Application, cylinder type, working fluid
3. **Technical Parameters** - Pressure, stroke, bore, rod, seals, temperature
4. **Construction** - Body/rod mounting, port types and positions
5. **Operating Conditions** - Duty cycle, loads, speed, frequency
6. **Materials & Coating** - Cylinder/rod materials, protective coatings
7. **Additional Requirements** - Sensors, valves, certifications, 3D model
8. **Logistics** - Quantity, delivery time, incoterms, packaging

---

## 🎨 Customization

### Branding Colors
Current brand colors (can be changed in CSS):
- **Primary Blue:** `#01577d`
- **Accent Blue:** `#0a6a94`
- **Accent Red:** `#bc3636`

### Email Templates
Edit in PHP handlers:
- Admin notification: `hydroforce_format_admin_email_en()`
- Client confirmation: `hydroforce_send_client_confirmation_en()`

### Form Fields
Add/remove fields in HTML, then update PHP handler to process them.

---

## 🌐 Multilingual Setup

Run **both** Russian and English forms simultaneously:

```php
// In functions.php
require_once get_template_directory() . '/functions-hydraulic-form.php';     // Russian
require_once get_template_directory() . '/functions-hydraulic-form-en.php';  // English
```

Create two pages:
- `/hydraulic-cylinder-request/` (Russian)
- `/en/hydraulic-cylinder-request/` (English)

Both will save to the same admin panel. English requests marked with `[EN]` prefix.

---

## 🔒 Security Features

- ✅ Nonce verification for AJAX requests
- ✅ Input sanitization with WordPress functions
- ✅ Email validation
- ✅ SQL injection prevention (WordPress handles this)
- ✅ XSS protection with `esc_html()`, `esc_attr()`
- ✅ CSRF protection with WordPress nonces

---

## 📊 Admin Panel Features

### Request List View
Shows all requests with sortable columns:
- Company name
- Contact person
- Email (clickable mailto link)
- Phone
- Cylinder type
- Submission date

### Individual Request View
Full details including:
- All contact information
- Complete technical specifications
- Raw JSON data for reference
- Edit capability

### Settings Page
Configure:
- Email address for notifications
- (Expandable for future settings)

---

## 🧪 Testing Checklist

- [ ] Form displays correctly
- [ ] All fields accept input
- [ ] Conditional fields show/hide properly
- [ ] Required field validation works
- [ ] Submit button triggers loading animation
- [ ] Success message appears after submission
- [ ] Admin receives email notification
- [ ] Client receives confirmation email
- [ ] Request appears in WordPress admin
- [ ] All data is saved correctly
- [ ] Mobile responsive layout works
- [ ] Form works in different browsers

---

## 🛠️ Technical Requirements

### Server Requirements:
- PHP 7.4 or higher
- WordPress 5.8+ (for WordPress integration)
- MySQL 5.7+ or MariaDB 10.2+
- PHP mail() function or SMTP plugin

### Browser Support:
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+
- Mobile browsers (iOS Safari, Chrome Mobile)

---

## 📞 Support & Maintenance

### Common Issues:

**Forms not submitting:**
- Check browser console for JavaScript errors
- Verify AJAX action name matches PHP handler
- Check WordPress debug log

**Emails not arriving:**
- Install WP Mail SMTP plugin
- Check spam folders
- Verify server can send emails

**Styling issues:**
- Clear browser cache
- Check CSS is loaded
- Verify no CSS conflicts with theme

---

## 📈 Future Enhancements

Possible improvements:
- [ ] File upload for drawings/photos
- [ ] PDF generation of requests
- [ ] Email to client with their submitted data
- [ ] Integration with CRM systems
- [ ] Analytics tracking
- [ ] Multi-step wizard interface
- [ ] Save draft functionality
- [ ] Admin dashboard widget
- [ ] Export to CSV/Excel

---

## 📝 Version History

### Version 1.0 (Current)
- ✅ Russian form (`Form_hc.html`)
- ✅ English form (`Form_hc_en.html`)
- ✅ WordPress integration
- ✅ Email notifications
- ✅ Custom Post Type
- ✅ Admin interface

---

## 📄 License

© 2024 Hydroforce. All rights reserved.

---

## 🎯 Quick Reference

### File Locations (WordPress):
```
wp-content/themes/your-theme/
├── functions.php                         ← Include handlers here
├── functions-hydraulic-form-en.php       ← English handler
├── functions-hydraulic-form.php          ← Russian handler
└── style.css                             ← Add form CSS here
```

### Key Functions (PHP):
- `hydroforce_handle_hydraulic_form_submission_en()` - Main AJAX handler
- `hydroforce_save_hydraulic_request_en()` - Save to database
- `hydroforce_send_admin_notification_en()` - Admin email
- `hydroforce_send_client_confirmation_en()` - Client email

### Key Variables (JavaScript):
- `hydroforce_ajax.ajax_url` - WordPress AJAX endpoint
- `hydroforce_ajax.nonce` - Security token
- Action: `submit_hydraulic_form_en` - AJAX action name (English)
- Action: `submit_hydraulic_form` - AJAX action name (Russian)

---

**For detailed setup instructions, see:**
- 🇬🇧 English: `INSTALLATION_INSTRUCTIONS.md`
- 🇷🇺 Russian: `ИНСТРУКЦИЯ.md`
