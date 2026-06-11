# 🔧 TECHNICAL DOCUMENTATION — VOID ARTS Commission Site

## **SYSTEM ARCHITECTURE**

### Single-File Application
- **Type:** Self-contained HTML5 application
- **Storage:** Browser LocalStorage API
- **No Backend Required:** Fully client-side
- **No Dependencies:** Pure JavaScript, HTML, CSS
- **Size:** ~110 KB (highly optimized)

---

## **DATA STRUCTURE**

### LocalStorage Keys

```javascript
va_codes              // Staff access codes
va_users              // User accounts
va_comms              // Commission types
va_queue              // Commission queue
va_reviews            // Client reviews
va_msgs               // Private messages
va_gchat              // Global chat
va_bans               // Ban list
va_gallery            // Portfolio images
va_videos             // Speed paint videos
va_freebies           // Free download files
va_channels           // Chat channels
va_profanity          // Blocked words
va_orders             // Commission orders
va_session            // Current user session
va_dev                // Device ID (for bans)
```

### Data Objects

#### User Object
```javascript
{
  id: "u123",
  username: "artistname",
  password: "hashedpassword",
  email: "artist@example.com",
  banned: false,
  banReason: "",
  joinDate: "2024-01-15"
}
```

#### Commission Object
```javascript
{
  id: "c123",
  title: "Full Body Character",
  category: "Character Design",
  desc: "Full body illustration...",
  price: 1800,
  status: "open", // open, closed, waitlist
  tags: ["character", "full body"],
  delivery: "7-10 days"
}
```

#### Order Object
```javascript
{
  id: "o123",
  user: "clientname",
  type: "Full Body Character",
  desc: "Dark elf warrior...",
  status: "pending", // pending, in_progress, completed
  date: "2024-01-15",
  price: 1800,
  source: "Website",
  deadline: "Standard (Artist's pace)",
  notes: "Extra details...",
  refs: "https://..."
}
```

#### Queue Item Object
```javascript
{
  id: "q123",
  user: "clientname",
  type: "Full Body Character",
  status: "pending", // pending, inprogress, done
  date: "2024-01-15"
}
```

#### Review Object
```javascript
{
  id: "r123",
  user: "clientname",
  rating: 5,
  type: "Full Body Character",
  text: "Amazing work!",
  date: "2024-01-15",
  approved: true
}
```

#### Message Object
```javascript
{
  sender: "username", // or "admin"
  text: "Message content",
  time: "14:30"
}
```

#### Channel Object
```javascript
{
  id: "ch123",
  name: "general",
  type: "text", // or "voice"
  msgs: [],
  users: []
}
```

---

## **KEY FUNCTIONS**

### Data Management
```javascript
gd(key, defaultValue)     // Get data from LocalStorage
sd(key, value)            // Save data to LocalStorage
uid()                     // Generate unique ID
fmtDate()                 // Format current date
fmtTime()                 // Format current time
```

### Authentication
```javascript
doLogin()                 // User login
doReg()                   // User registration
doStaff()                 // Staff login with code
doLogout()                // Logout user
updateUI()                // Update UI based on auth state
checkBan()                // Check if user is banned
```

### Navigation
```javascript
go(pageId)                // Navigate to page
showPage(id)              // Same as go()
openAuth()                // Open login modal
om(modalId)               // Open modal
cm(modalId)               // Close modal
```

### Commissions
```javascript
renderComms()             // Display commission grid
filterC(category, btn)    // Filter by category
openOrd(commissionId)     // Open order modal
submitOrd()               // Submit order
openAddCM()               // Open add commission modal
editCM(id)                // Edit commission
saveCM()                  // Save commission
toggleCM(id)              // Toggle status
delCM(id)                 // Delete commission
```

### Queue
```javascript
renderQueue()             // Display queue
setQS(id, status)         // Set queue status
delQ(id)                  // Remove from queue
```

### Gallery
```javascript
renderGallery()           // Display gallery
handleGLUp(event)         // Handle image upload
addGLItem()               // Add gallery item
delGL(id)                 // Delete gallery item
openLB(url, title)        // Open lightbox
```

### Videos
```javascript
renderVideos()            // Display videos
handleVDUp(event)         // Handle video upload
addVideo()                // Add video
delVD(id)                 // Delete video
playV(button, videoId)    // Play/pause video
```

### Freebies
```javascript
renderFreebies()          // Display freebies
handleFBUp(event)         // Handle file upload
addFB()                   // Add freebie
delFB(id)                 // Delete freebie
dlFree(id)                // Download file
```

### Reviews
```javascript
renderReviews()           // Display reviews
setRating(n)              // Set star rating
submitRv()                // Submit review
toggleRV(id)              // Approve/hide review
delRV(id)                 // Delete review
```

### Chat
```javascript
renderGC()                // Render global chat
toggleGC()                // Toggle chat open/close
sendGC()                  // Send global message
renderChat()              // Render private chat
selChat(userId)           // Select chat user
sendPriv()                // Send private message
```

### Channels
```javascript
renderChSidebar()         // Display channel list
openCh(channelId)         // Open channel
renderTextCh(ch, main)    // Render text channel
renderVoiceCh(ch, main)   // Render voice channel
sendChMsg(channelId)      // Send channel message
addChModal(type)          // Open add channel modal
confirmAddCh()            // Create channel
delCh(id)                 // Delete channel
toggleMic()               // Toggle microphone
toggleSS()                // Toggle screen share
stopSS()                  // Stop screen sharing
leaveVoice()              // Leave voice channel
```

### Admin Panel
```javascript
buildAdminNav()           // Build admin sidebar
switchATab(tab, el)       // Switch admin tab
renderATab(tab)           // Render admin tab
aTabDash(c, H)            // Dashboard
aTabComms(c, H)           // Commissions
aTabOrders(c, H)          // Orders
aTabQueue(c, H)           // Queue
aTabUsers(c, H)           // Users
aTabGallery(c, H)         // Gallery
aTabVideos(c, H)          // Videos
aTabFreebies(c, H)        // Freebies
aTabReviews(c, H)         // Reviews
aTabChannels(c, H)        // Channels
aTabBans(c, H)            // Bans
aTabProfanity(c, H)       // Profanity
aTabCodes(c, H)           // Staff codes (owner)
aTabRanks(c, H)           // Ranks (owner)
aTabSettings(c, H)        // Settings
```

### Moderation
```javascript
filterProf(text)          // Filter profanity
addBan()                  // Ban user
removeBan(id)             // Unban user
banU(userId)              // Ban user account
unbanU(userId)            // Unban user account
delU(userId)              // Delete user
addPF()                   // Add profanity word
delPF(word)               // Remove profanity word
```

### Staff Management (Owner)
```javascript
addSCode()                // Add staff code
revokeSCode(id)           // Revoke staff code
createRank()              // Create new rank
```

### Utility
```javascript
readFileAsDataURL(file, callback)  // Read file as base64
serr(id, message)         // Show error message
toast(message)            // Show toast notification
setTheme(themeName)       // Change theme
```

### Animation
```javascript
initBH()                  // Initialize blackhole
initStars()               // Initialize starfield
```

---

## **CSS VARIABLES**

### Colors
```css
--void: #000              // Pure black
--deep: #050508           // Very dark
--abyss: #0a0a12          // Dark blue-black
--dark: #0d0d1a           // Dark
--surface: #12121f        // Surface
--card: #16162a           // Card background
--card2: #1a1a30          // Card hover
--border: rgba(255,255,255,0.07)    // Light border
--border2: rgba(255,255,255,0.15)   // Lighter border
--white: #fff             // White
--ghost: rgba(255,255,255,0.6)      // 60% white
--muted: rgba(255,255,255,0.35)     // 35% white
--faint: rgba(255,255,255,0.1)      // 10% white
--red: #e53935            // Main red
--red2: #ff1744           // Bright red
--blue: #1565c0           // Dark blue
--blue2: #2979ff          // Bright blue
--cyan: #00e5ff           // Cyan
--gold: #ffd700           // Gold
```

### Fonts
```css
--font-title: 'Cinzel'     // Title font
--font-body: 'Rajdhani'    // Body font
--font-mono: 'Share Tech Mono'  // Monospace
```

---

## **BROWSER COMPATIBILITY**

✓ Chrome/Chromium (latest)
✓ Firefox (latest)
✓ Safari (latest)
✓ Edge (latest)
✓ Mobile browsers

**Requirements:**
- LocalStorage API
- File API (for uploads)
- Canvas API (for animations)
- ES6+ JavaScript support

---

## **FILE UPLOAD HANDLING**

### Process
1. User selects file via input
2. `FileReader` reads file as Data URL
3. Base64 encoded string stored in LocalStorage
4. Stored in `_glData`, `_vdData`, `_fbData`
5. Displayed via `src` attribute
6. Saved to respective storage key

### Supported Formats
- **Images:** JPG, PNG, GIF, WEBP
- **Videos:** MP4, WebM, MOV, AVI, MKV, etc.
- **Files:** Any format (ZIP, PDF, etc.)

### Size Limitations
- LocalStorage limit: ~5-10MB (varies by browser)
- Large files may not store
- Split across multiple keys if needed

---

## **PROFANITY FILTER IMPLEMENTATION**

```javascript
filterProf(text) {
  let list = gd('va_profanity',[]);
  let bad = false;
  let out = text;
  
  list.forEach(word => {
    const rx = new RegExp(word, 'gi');
    if (rx.test(out)) {
      bad = true;
      out = out.replace(rx, '*'.repeat(word.length));
    }
  });
  
  return { text: out, bad: bad };
}
```

Applied to:
- Order descriptions ✓
- Reviews ✓
- Chat messages (global) ✓
- Channel messages ✓
- Private messages ✓

---

## **THEME SYSTEM**

### Theme Switching
```javascript
setTheme(themeName) {
  // Changes CSS variables
  // Updates canvas opacity
  // Smooth color transitions
}
```

### Available Themes
1. **bh** - Blackhole (default)
2. **bw** - Black & White
3. **rb** - Red/Blue (Demon King)
4. **star** - Starfield

---

## **MODAL SYSTEM**

### Modal IDs
```javascript
m-auth          // Authentication
m-order         // Place order
m-aorder        // Add order (admin)
m-review        // Write review
m-comm          // Add/edit commission
m-codes         // Staff codes (owner)
m-addch         // Add channel
m-lb            // Lightbox
```

### Functions
```javascript
om(id)  // Open modal
cm(id)  // Close modal
```

---

## **ERROR HANDLING**

All data operations wrapped in try-catch:
```javascript
function gd(k,d) {
  try {
    const v = localStorage.getItem(k);
    return v ? JSON.parse(v) : d;
  } catch {
    return d;
  }
}
```

Storage errors show toast notification:
```javascript
toast('Storage full! Try clearing old media files.');
```

---

## **PERFORMANCE OPTIMIZATIONS**

✓ Minimized CSS
✓ Optimized JavaScript
✓ Lazy loading for images
✓ Canvas animations (GPU accelerated)
✓ Event delegation for modals
✓ Efficient DOM updates
✓ LocalStorage caching

---

## **DEVELOPMENT TIPS**

### Adding New Admin Tab
1. Add function `aTab[Name](c, H)`
2. Add case in `renderATab()`
3. Add nav item in `buildAdminNav()`
4. Follow existing pattern

### Adding New Data Type
1. Initialize in `window.onload`
2. Create helper functions
3. Add render function
4. Add to admin panel
5. Implement CRUD operations

### Debugging
Open browser DevTools (F12):
- **Console** - Check for errors
- **Application** - View LocalStorage
- **Network** - Check file uploads
- **Elements** - Inspect DOM

---

## **DEPLOYMENT**

### Single File Deployment
1. Upload `commission_site.html` to hosting
2. No backend needed
3. Works immediately
4. All data stored client-side

### Backup Data
```javascript
// Export all data
const backup = {
  users: gd('va_users',[]),
  comms: gd('va_comms',[]),
  orders: gd('va_orders',[]),
  // ... etc
};
console.log(JSON.stringify(backup));
```

---

## **SECURITY CONSIDERATIONS**

⚠️ **Important Notes:**
- All data stored in browser (not secure for sensitive info)
- Passwords stored in plaintext (use server auth in production)
- No encryption (add SSL for production)
- No audit logs (add server-side logging)
- Client-side only (easy to modify with DevTools)

### For Production:
✓ Implement server-side authentication
✓ Use HTTPS encryption
✓ Hash passwords
✓ Implement real database
✓ Add audit logging
✓ Validate all inputs server-side

---

**End of Technical Documentation**
