# 🎨 CUSTOMIZATION GUIDE — VOID ARTS Commission Site

## **EASY CUSTOMIZATION (No Coding Required)**

### **Within the Application**

#### Change Site Settings
1. Login as owner
2. Go to ⚙ PANEL
3. Click **Settings** tab
4. Change:
   - Commission Status Banner
   - Open Slots number
   - Artist's social media
   - Welcome messages

#### Create Custom Commissions
1. Go to **Commissions** tab
2. Click **+ ADD NEW TYPE**
3. Set:
   - Title
   - Category (custom names)
   - Description
   - Price
   - Status
   - Tags
   - Delivery time

#### Add Your Content
- **Gallery Tab:** Upload your artwork
- **Videos Tab:** Upload portfolio videos
- **Freebies Tab:** Add free downloads
- **Reviews Tab:** Moderate client reviews

#### Manage Community
- **Channels Tab:** Create text & voice channels
- **Global Chat:** Public messaging
- **Private Chat:** Admin to user messages

#### Customize Profanity Filter
- Go to **Profanity** tab
- Add words to block
- Remove overly strict words
- Customize for your community

---

## **COSMETIC CUSTOMIZATION (Minor Code Edits)**

### **Change Site Name**

**Step 1: Open in Text Editor**
1. Right-click `commission_site.html`
2. Select "Open with" → Notepad/VSCode
3. Find and replace:

**Find:** `VOID ARTS`
**Replace with:** `Your Studio Name`

**Where to change:**
- Line ~5: `<title>✦ VOID ARTS`
- Line ~70: `<div class="nav-logo">✦ VOID ARTS</div>`
- Line ~500: Inside hero section
- Line ~1200: In home page text

**Save:** Ctrl+S

---

### **Change Theme Colors**

**Step 1: Find CSS Variables**
Look for the `:root` section (around line 10):

```css
:root {
  --red: #e53935;
  --red2: #ff1744;
  --blue2: #2979ff;
  --cyan: #00e5ff;
  --gold: #ffd700;
}
```

**Step 2: Change Values**

| Color | Current | Purpose |
|-------|---------|---------|
| --red | #e53935 | Main accent color |
| --blue2 | #2979ff | Secondary accent |
| --cyan | #00e5ff | Highlight color |
| --gold | #ffd700 | Owner/special color |

**Step 3: Use Color Picker**
1. Go to colorpicker.com
2. Find color you want
3. Copy hex code
4. Paste into CSS

**Example:**
```css
--red: #ff0000;  /* Change to pure red */
--cyan: #00ff00; /* Change to pure green */
--gold: #ffff00; /* Change to yellow */
```

**Save and refresh browser**

---

### **Change Fonts**

**Current Fonts:**
- **Titles:** Cinzel (Google Fonts)
- **Body:** Rajdhani (Google Fonts)
- **Code:** Share Tech Mono (Google Fonts)

**Find CSS Variables:**
```css
--font-title: 'Cinzel';
--font-body: 'Rajdhani';
--font-mono: 'Share Tech Mono';
```

**Find Serif Fonts (replace Cinzel):**
- Georgia, Garamond, Times New Roman

**Find Sans-serif (replace Rajdhani):**
- Arial, Helvetica, Verdana

**Example:**
```css
--font-title: Georgia;
--font-body: Arial;
--font-mono: 'Courier New';
```

---

### **Change Text & Labels**

**Search and Replace**

| Find | Replace with | Where |
|------|--------------|-------|
| VOID ARTS | Your Name | Site title |
| VoidZero | Your Rank | Owner rank |
| COSMIC SINGULARITY | Your tagline | Hero section |
| Dark character design | Your focus | Home subtitle |

**Use Find & Replace:**
1. Ctrl+H in text editor
2. Enter "Find" text
3. Enter "Replace" text
4. Click "Replace All"
5. Save file

---

### **Change Favicon (Tab Icon)**

1. Create icon image (32x32px)
2. Convert to .ico file (icoconvert.com)
3. Put in same folder as HTML
4. Add this line after `<title>`:

```html
<link rel="icon" href="favicon.ico" type="image/x-icon">
```

---

## **ADVANCED CUSTOMIZATION (Code Skills Required)**

### **Add Custom Themes**

**Find setTheme() function** (around line 1350):

```javascript
function setTheme(t) {
  // Existing themes: bh, bw, rb, star
  // Add new theme here
}
```

**Add new theme:**

```javascript
else if(t==='purple') {
  setV('#9c27b0', '#e040fb', '#7c4dff', '#ba68c8', '#d946ef');
  // setV(red, red2, blue2, cyan, gold)
}
```

**Add theme button in HTML:**

```html
<div class="tswb" data-t="purple" onclick="setTheme('purple')"></div>
```

---

### **Modify Admin Tabs**

**Find renderATab() function** (around line 1020):

```javascript
function renderATab(tab) {
  switch(tab) {
    case 'dashboard': // existing
    case 'custom': customAdminTab(c, H); break; // your new tab
  }
}
```

**Add your custom function:**

```javascript
function customAdminTab(c, H) {
  c.innerHTML = H('Custom Tab') + `
    <p>Your custom content here</p>
  `;
}
```

---

### **Add New Page**

**Step 1: Add HTML page section**

```html
<div id="page-custom" class="page">
  <div class="sec">
    <h2 class="sectitle">Custom Page</h2>
    <div id="custom-content"></div>
  </div>
</div>
```

**Step 2: Add navigation button**

```html
<button class="nb" onclick="go('custom')">CUSTOM</button>
```

**Step 3: Add render function**

```javascript
function renderCustom() {
  document.getElementById('custom-content').innerHTML = `
    Your HTML here
  `;
}
```

**Step 4: Call from go() function**

```javascript
if(id==='custom') renderCustom();
```

---

### **Modify Database Structure**

**Add new data type:**

```javascript
// In window.onload:
!gd('va_custom', null) && sd('va_custom', [
  {id: 'item1', name: 'Example', data: {}}
]);
```

**Access data:**

```javascript
const data = gd('va_custom', []);
sd('va_custom', data); // Save after changes
```

---

## **LAYOUT CUSTOMIZATION**

### **Change Hero Section**

Find hero section (around line 400):

```html
<div id="hero">
  <h1 class="htitle">
    <span>VOID</span>
    <span>ARTS</span>
  </h1>
</div>
```

**Customize:**
- Change title text
- Change subtitle
- Modify stats
- Add/remove sections

---

### **Modify Navigation Bar**

Find nav section (around line 70):

```html
<nav>
  <button class="nb" onclick="go('home')">HOME</button>
  <!-- Add more buttons here -->
</nav>
```

**Add custom navigation items:**

```html
<button class="nb" onclick="go('custom')">YOUR PAGE</button>
```

---

### **Customize Admin Sidebar**

Find buildAdminNav() function (around line 1005):

```javascript
const items = [
  ['dashboard', '📊', 'Dashboard'],
  // Add your own items:
  ['custom', '⭐', 'Custom Feature'],
];
```

---

## **RESPONSIVE DESIGN MODIFICATIONS**

### **Change Mobile Breakpoints**

Find media queries in CSS:

```css
/* Change from auto-fill to specific columns */
.cgrid {
  grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
  /* Change to: */
  grid-template-columns: repeat(2, 1fr); /* 2 columns */
}
```

---

## **ANIMATION CUSTOMIZATION**

### **Blackhole Animation**

Find initBH() function (around line 1400):

```javascript
const r = Math.min(W, H) * 0.12; // Radius
// Increase to make bigger: * 0.15
// Decrease to make smaller: * 0.10

const cx = W * 0.65; // Horizontal position
// 0.65 = right side, 0.5 = center, 0.35 = left side
```

### **Starfield Animation**

Find initStars() function (around line 1450):

```javascript
for(let i = 0; i < 300; i++) // Number of stars
// Change 300 to more stars (slower) or fewer (faster)

s.r = Math.random() * 1.5 + 0.2; // Star size
// Increase 1.5 to make bigger stars
```

---

## **CUSTOMIZATION EXAMPLES**

### **Example 1: Change Primary Color**

```css
--red: #ff6b6b;        /* Your custom red */
--red2: #ff8787;       /* Lighter red */
--glow-r: 0 0 20px rgba(255, 107, 107, 0.4); /* Update glow too */
```

### **Example 2: Change Site Name**

Find all instances:
1. Title tag: `<title>✦ Your Name`
2. Nav logo: `.nav-logo` text
3. Hero: `htitle` text

### **Example 3: Customize Commission Categories**

In admin panel (no code needed):
1. Add commissions with custom categories
2. Categories auto-generate filters
3. No code changes needed!

### **Example 4: Add Custom Admin Tab**

1. Add case in renderATab()
2. Create tab function
3. Add nav item in buildAdminNav()
4. Render content dynamically

---

## **PERFORMANCE OPTIMIZATION**

### **Reduce Animation**

If site is slow:

```css
@keyframes qp {
  /* Make animation shorter/simpler */
  0% { opacity: 1; }
  100% { opacity: 0.8; }
}
```

Or disable animations entirely:

```javascript
// In initBH and initStars:
// Comment out requestAnimationFrame calls
```

### **Optimize Images**

1. Keep images under 500KB each
2. Use JPG for photos
3. Use PNG for graphics
4. Compress images first

### **Clean Old Data**

1. Delete old videos
2. Delete old files
3. Archive old orders
4. Export and clear LocalStorage

---

## **BACKUP BEFORE CUSTOMIZING**

**Always backup original!**

1. Save copy: `commission_site_backup.html`
2. Keep original safe
3. Customize the copy
4. If issues, revert to original

---

## **CSS CLASS REFERENCE**

### Common Elements

```css
.htitle    /* Hero title */
.hsub      /* Hero subtitle */
.bprimary  /* Primary button */
.sectitle  /* Section title */
.ctitle    /* Commission card title */
.nbadge    /* Navigation button */
.ccard     /* Commission card */
.rcard     /* Review card */
.mbox      /* Modal box */
```

### Modify Styles

Find class in `<style>` section and change properties:

```css
.bprimary {
  background: your-color;
  padding: new-size;
  border-radius: new-shape;
}
```

---

## **RECOMMENDED CUSTOMIZATIONS**

1. **Site Name** (Easy)
   - Change "VOID ARTS" to your name
   - 5 minutes

2. **Colors** (Easy)
   - Change accent colors
   - 10 minutes

3. **Hero Text** (Easy)
   - Customize subtitle and tagline
   - 5 minutes

4. **Commission Types** (Easy, no code)
   - Add yours via admin panel
   - 20 minutes

5. **Fonts** (Medium)
   - Choose from Google Fonts
   - 15 minutes

6. **Custom Theme** (Hard)
   - Create new theme variant
   - 30 minutes

7. **New Admin Tab** (Hard)
   - Add custom feature
   - 1 hour+

---

## **TESTING CUSTOMIZATIONS**

1. Make a backup
2. Change one thing
3. Save file
4. Refresh browser (Ctrl+F5)
5. Check if it works
6. If not, revert change
7. Try different approach

---

## **CUSTOMIZATION CHECKLIST**

- [ ] Backup original file
- [ ] Change site name
- [ ] Customize colors
- [ ] Add commissions
- [ ] Upload images
- [ ] Test all features
- [ ] Verify mobile looks good
- [ ] Check animations
- [ ] Ready to deploy!

---

**Happy Customizing! 🎨**
