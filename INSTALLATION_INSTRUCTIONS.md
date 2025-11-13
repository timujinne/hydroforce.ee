# Hydraulic Cylinder Form - Installation Instructions

## 📋 Files Overview

### HTML Forms:
- **`Form_hc.html`** - Russian version (Русская версия)
- **`Form_hc_en.html`** - English version (Английская версия)

### WordPress PHP Handlers:
- **`functions-hydraulic-form.php`** - Russian handler (existing)
- **`functions-hydraulic-form-en.php`** - English handler (NEW)

---

## 🔧 Installation Steps

### Option 1: WordPress Integration (Recommended)

#### Step 1: Add PHP Functions to WordPress

Add the contents of **`functions-hydraulic-form-en.php`** to your theme's `functions.php` file:

**Location:** `wp-content/themes/your-theme/functions.php`

```php
// Copy entire content from functions-hydraulic-form-en.php
// OR include it:
require_once get_template_directory() . '/functions-hydraulic-form-en.php';
```

#### Step 2: Create WordPress Page

1. Go to WordPress Admin → Pages → Add New
2. Title: "Hydraulic Cylinder Request Form" (or any title)
3. Switch to HTML/Code editor
4. Copy the **BODY content only** from `Form_hc_en.html` (from `<div class="container">` to end of `</script>`)
5. Paste into page content
6. Publish page

#### Step 3: Add Styles to Theme

Add the CSS from `Form_hc_en.html` (everything inside `<style>` tags) to your theme's style sheet:

**Location:** `wp-content/themes/your-theme/style.css`

OR create a custom CSS file and enqueue it in `functions.php`:

```php
function hydroforce_form_styles() {
    wp_enqueue_style('hydraulic-form', get_template_directory_uri() . '/css/hydraulic-form.css');
}
add_action('wp_enqueue_scripts', 'hydroforce_form_styles');
```

#### Step 4: Update AJAX Action Name

In the HTML form JavaScript (around line 52 in `Form_hc_en.html`), change the action:

```javascript
// CHANGE THIS:
formDataToSend.append('action', 'submit_hydraulic_form');

// TO THIS (for English version):
formDataToSend.append('action', 'submit_hydraulic_form_en');
```

---

### Option 2: Standalone HTML (No WordPress)

If you're NOT using WordPress, you can use the form standalone:

#### What happens:
- Form collects data
- Shows "Demo Mode" message
- Data is logged to browser console
- No email is sent

#### To enable email sending without WordPress:
You need to create a separate PHP email handler (contact a developer).

---

## ⚙️ Configuration

### Email Settings

By default, emails are sent to the WordPress admin email. To change:

1. Go to WordPress Admin
2. Navigate to: **Hydraulic Requests → Settings**
3. Enter custom email address
4. Save

### Email Addresses to Update

In `functions-hydraulic-form-en.php`, update these lines if needed:

```php
// Line ~320 (Client confirmation email)
<li>Email: info@hydroforce.ee</li>
<li>Phone: +372 XXX XXXX</li>  // ← UPDATE YOUR PHONE
```

---

## 📧 How It Works

### User Flow:
1. User fills out form on website
2. Clicks "Submit Request"
3. Loading animation appears
4. Data sent via AJAX to WordPress

### Backend Processing:
1. WordPress receives AJAX request
2. Validates all required fields
3. Saves to Custom Post Type "Hydraulic Requests"
4. Sends 2 emails:
   - **Admin email** - Full request details with link to admin panel
   - **Client email** - Confirmation message

### Admin Panel:
- View all requests: **WP Admin → Hydraulic Requests**
- See columns: Company, Contact, Email, Phone, Cylinder Type, Date
- Click request to view full details
- All data is searchable and filterable

---

## 🔍 Testing

### Test in Demo Mode (Before WordPress Integration):
1. Open `Form_hc_en.html` in browser
2. Fill out form
3. Submit
4. Should see: "Demo Mode: Form collected data successfully!"
5. Check browser console (F12) for collected data

### Test in WordPress:
1. Open form page on your WordPress site
2. Fill out form (use real email for testing)
3. Submit
4. Should see: "Thank you! Your request has been successfully submitted..."
5. Check:
   - WP Admin → Hydraulic Requests (new entry should appear)
   - Your admin email inbox (should receive notification)
   - Test customer email inbox (should receive confirmation)

---

## 🐛 Troubleshooting

### Form shows "Demo Mode" message:
- **Cause:** WordPress AJAX not detected
- **Fix:** Make sure `hydroforce_enqueue_form_scripts()` is running (check `functions.php`)

### Email not sending:
- **Cause:** WordPress mail() function not working
- **Fix:** Install SMTP plugin (e.g., "WP Mail SMTP")
- Check spam folder

### Form not submitting:
- **Check browser console** (F12 → Console tab) for errors
- **Verify AJAX action name** matches PHP function name
- **Check nonce** is being generated correctly

### "Security error" message:
- **Cause:** Nonce verification failed
- **Fix:** Clear cache and refresh page
- Check that `wp_create_nonce('hydraulic_form_nonce')` is working

---

## 📁 File Structure in WordPress

```
wp-content/
└── themes/
    └── your-theme/
        ├── functions.php                    (include PHP handler here)
        ├── functions-hydraulic-form-en.php  (English handler)
        ├── style.css or custom CSS file     (form styles)
        └── page-templates/
            └── form-page.php                (optional: custom template)
```

---

## 🌐 Multilingual Setup

### If you have BOTH Russian and English forms:

#### In `functions.php`, include both handlers:
```php
require_once get_template_directory() . '/functions-hydraulic-form.php';     // Russian
require_once get_template_directory() . '/functions-hydraulic-form-en.php';  // English
```

#### Create 2 separate pages:
- **Russian page:** Uses `Form_hc.html` → AJAX action: `submit_hydraulic_form`
- **English page:** Uses `Form_hc_en.html` → AJAX action: `submit_hydraulic_form_en`

#### Both forms will:
- Save to same Custom Post Type
- Show in same admin list
- English requests marked with `[EN]` prefix in title

---

## 📝 Customization

### Change Form Fields:
1. Edit HTML in `Form_hc_en.html`
2. Update PHP handlers to process new fields
3. Update email templates to display new fields

### Change Email Templates:
Edit functions in `functions-hydraulic-form-en.php`:
- `hydroforce_format_admin_email_en()` - Admin notification
- `hydroforce_send_client_confirmation_en()` - Client confirmation

### Change Success Message:
In `Form_hc_en.html`, find line with `successMsg.textContent`

---

## 🚀 Going Live Checklist

- [ ] Test form submission
- [ ] Verify admin email received
- [ ] Verify client confirmation received
- [ ] Check spam folders
- [ ] Test with real email addresses
- [ ] Check admin panel shows request
- [ ] Verify all required fields work
- [ ] Test on mobile devices
- [ ] Update contact phone/email in confirmation
- [ ] Set up SMTP plugin for reliable email delivery

---

## 📞 Support

If you need help:
1. Check browser console for errors (F12)
2. Check WordPress debug log
3. Contact your developer

---

## 📄 License

© 2024 Hydroforce. All rights reserved.
