# ❓ FAQ & TROUBLESHOOTING — VOID ARTS Commission Site

## **FREQUENTLY ASKED QUESTIONS**

### **Q: Do I need a server to run this?**
A: No! This is a single HTML file that runs entirely in your browser. Just open it and it works immediately. All data is stored locally on your device.

### **Q: Can I share this with clients?**
A: Yes! Send them the HTML file or upload it to any web hosting (Netlify, GitHub Pages, Vercel, etc.). It works everywhere.

### **Q: What's the owner code?**
A: **13072006aA!** - Use this to login as owner. Keep it secret!

### **Q: Can I change the owner code?**
A: Not recommended in the code - it's hardcoded. For production, you'd want to hash it. For now, keep it secure.

### **Q: Will my data be saved?**
A: Yes! All data is saved to your browser's LocalStorage. It persists after page refresh. BUT if you clear browser cache, data is lost!

### **Q: Should I backup my data?**
A: Yes! Regularly export your data by opening DevTools (F12) → Application → LocalStorage. Copy all keys and save as JSON backup file.

### **Q: Can I delete users?**
A: Yes! Go to Admin Panel → Users → click DEL button to delete a user account.

### **Q: Can multiple people edit at once?**
A: No - this is client-side only. If multiple people access simultaneously, the last one to save wins. For production, use a real database.

### **Q: How do I make staff accounts?**
A: Owner only! Go to Admin Panel → Staff Codes → Add code → Give staff the code → They login with it.

### **Q: Can staff delete other staff?**
A: Only the Owner can revoke staff codes. Regular staff cannot delete other staff.

### **Q: How does screen sharing work?**
A: It's simulated - shows the screen share interface. For real screen sharing, implement WebRTC (requires backend).

### **Q: Can clients place orders anonymously?**
A: No - they must login first. But they can register with any email.

### **Q: What file formats are supported?**

Images (Gallery):
- JPG, PNG, GIF, WEBP

Videos:
- MP4, WebM, MOV, AVI, MKV, etc.

Freebies:
- Any file type (ZIP, PDF, PSD, BRUSH, etc.)

### **Q: Can I upload really large files?**
A: Browser LocalStorage has ~5-10MB limit. Large videos/files might not store. Consider using external URLs instead.

### **Q: How do I change the site name?**
A: Edit the HTML in a text editor. Find "VOID ARTS" and replace with your name.

### **Q: Can I customize the colors?**
A: Yes! Find CSS variables in the `<style>` section and edit the color values.

### **Q: How do I add more themes?**
A: Edit the `setTheme()` function and add a new color scheme.

### **Q: Can I use this commercially?**
A: Yes! It's yours to use and modify.

---

## **TROUBLESHOOTING**

### **❌ Problem: Data disappeared after refresh**
**Cause:** Browser cache was cleared or cookies disabled
**Solution:** 
1. Don't clear cache while using the site
2. Check if LocalStorage is enabled:
   - Open DevTools (F12)
   - Go to Application tab
   - Check LocalStorage
3. Enable persistent storage if available

### **❌ Problem: Can't upload files**
**Cause:** File too large or wrong format
**Solution:**
1. Try a smaller file
2. Check file format is correct
3. Clear browser cache (if storage is full)
4. Try a different browser
5. Use URL instead of uploading

### **❌ Problem: Video won't play**
**Cause:** File format not supported or encoding issue
**Solution:**
1. Try MP4 format (most compatible)
2. Convert video using Handbrake (free)
3. Use external URL (YouTube, Vimeo)
4. Check browser console for errors (F12)

### **❌ Problem: Chat messages not appearing**
**Cause:** LocalStorage issue
**Solution:**
1. Refresh page (F5)
2. Check DevTools → Application → LocalStorage
3. Clear cache and try again
4. Make sure you're logged in

### **❌ Problem: Can't login**
**Cause:** Wrong credentials or account banned
**Solution:**
1. Check username/password spelling
2. Try registering new account
3. Check if account is banned (try different name)
4. Clear cookies and try again

### **❌ Problem: "Access Denied" message**
**Cause:** User/IP/Device is banned
**Solution:**
1. You've been banned from the site
2. Contact admin/owner for appeal
3. Use different account
4. Clear cookies and register new account

### **❌ Problem: Admin panel not showing**
**Cause:** Not logged in as staff
**Solution:**
1. Login with owner code: 13072006aA!
2. Or create staff code first
3. Click ⚙ PANEL button (should be gold if owner)

### **❌ Problem: Commission won't appear in list**
**Cause:** Status set to closed
**Solution:**
1. Go to Admin → Commissions
2. Find commission
3. Click TOGGLE to change status to "open"

### **❌ Problem: Can't see user in DM list**
**Cause:** User hasn't registered yet
**Solution:**
1. User must register first
2. Only registered users appear in list
3. Create demo accounts if testing

### **❌ Problem: Theme colors not changing**
**Cause:** Browser cache needs refresh
**Solution:**
1. Hard refresh (Ctrl+Shift+R on Windows, Cmd+Shift+R on Mac)
2. Clear cache and cookies
3. Try different browser

### **❌ Problem: Animations lagging/stuttering**
**Cause:** Older browser or low performance
**Solution:**
1. Update browser to latest version
2. Close other tabs
3. Disable other extensions
4. Try Chrome (best performance)
5. Reduce canvas effects in CSS

### **❌ Problem: File upload says "Storage full"**
**Cause:** LocalStorage exceeded ~5-10MB limit
**Solution:**
1. Delete old files (gallery, videos, freebies)
2. Use external URLs instead of uploading
3. Clear browser cache
4. Use different browser
5. Split data across multiple devices

### **❌ Problem: Button not responding**
**Cause:** JavaScript error or modal blocking
**Solution:**
1. Refresh page (F5)
2. Check if modal is open (close with X button)
3. Open DevTools (F12) → Console tab
4. Look for error messages
5. Try different browser

### **❌ Problem: Forms not submitting**
**Cause:** Validation error or missing field
**Solution:**
1. Check error message at top of form
2. Fill all required fields
3. Check for profanity in text (might auto-block)
4. Try refreshing page
5. Clear form and try again

### **❌ Problem: Queue shows wrong position**
**Cause:** Browser cache or data sync issue
**Solution:**
1. Refresh page (F5)
2. Check if order was actually submitted
3. Check Admin → Orders to verify
4. Try logging out and back in

---

## **COMMON ISSUES & FIXES**

### Issue: "Out of memory" error
- Clear browser cache
- Close other browser tabs
- Restart browser
- Try different browser

### Issue: Page loads blank/white
- Wait 2-3 seconds (animations loading)
- F5 refresh
- Ctrl+Shift+Delete (clear cache)
- Check browser console for errors

### Issue: Text size too small on phone
- Zoom in (pinch gesture)
- Check if zoom is set correctly
- Try landscape orientation
- Use Chrome mobile

### Issue: Images appear blurry
- File might be low resolution
- Re-upload higher quality image
- Check image dimensions (aim for 1024px+)

### Issue: Videos not playing on phone
- Use MP4 format
- Video might be too large
- Try YouTube embed instead
- Check mobile browser compatibility

### Issue: Profanity filter too strict
- Words being blocked wrongly
- Add safe words to filter words list
- Remove unnecessary words from filter
- Go to Admin → Profanity

### Issue: Can't find where to add commission
- Click ⚙ PANEL (admin)
- Go to Commissions tab
- Click + ADD NEW TYPE
- Fill in details

---

## **PERFORMANCE TIPS**

✓ **Optimize performance:**
- Delete old media files regularly
- Keep video files under 50MB
- Use JPG for images (not PNG)
- Use URL for large files (don't upload)
- Close other browser tabs
- Update browser to latest version

✓ **Improve speed:**
- Clear browser cache monthly
- Reduce number of animations
- Disable effects if laggy
- Use Chrome browser (fastest)
- Don't store 1000+ messages

✓ **Backup data regularly:**
- Export LocalStorage every month
- Save JSON backup file
- Use multiple backup locations
- Test restore process

---

## **ADVANCED TROUBLESHOOTING**

### Check Browser Console (F12)
```javascript
// View all data
Object.keys(localStorage)

// Check specific data
JSON.parse(localStorage.getItem('va_users'))

// Clear all data (WARNING: permanent!)
localStorage.clear()

// Count stored items
Object.keys(localStorage).length
```

### Fix Corrupted Data
```javascript
// Reset to defaults (WARNING: loses everything!)
localStorage.clear();
location.reload();
```

### Export Backup
```javascript
// In console, run:
const backup = {};
Object.keys(localStorage).forEach(key => {
  backup[key] = localStorage.getItem(key);
});
console.log(JSON.stringify(backup));
// Copy output and save to file
```

### Import Backup
```javascript
// In console, paste and run:
const backup = {/* paste your backup here */};
Object.keys(backup).forEach(key => {
  localStorage.setItem(key, backup[key]);
});
location.reload();
```

---

## **BROWSER DEVELOPER TOOLS**

### Open DevTools
- **Windows:** F12 or Ctrl+Shift+I
- **Mac:** Cmd+Option+I
- **Right-click:** Inspect

### Useful Tabs
- **Console:** Check errors, run code
- **Application:** View LocalStorage data
- **Network:** Check file uploads
- **Elements:** Inspect HTML structure

### View LocalStorage
1. Open DevTools (F12)
2. Click "Application" tab
3. Click "Local Storage" in left panel
4. Click the website URL
5. View all stored data

---

## **GETTING HELP**

### Before reporting issue:
1. ✓ Refresh page (F5)
2. ✓ Clear cache (Ctrl+Shift+Delete)
3. ✓ Try different browser
4. ✓ Try incognito/private mode
5. ✓ Check browser console for errors
6. ✓ Check this guide

### When reporting:
- Describe exactly what happened
- Include error message (screenshot)
- List browser/device used
- List steps to reproduce
- Attach backup of data

---

## **QUICK REFERENCE**

| Issue | Quick Fix |
|-------|-----------|
| Data missing | Clear cache disabled = lost data (needs backup) |
| Can't login | Register new account |
| Admin not showing | Use owner code: 13072006aA! |
| File too large | Use external URL instead |
| Slow performance | Close tabs, clear cache, update browser |
| Button not working | Refresh page, check modal |
| Chat not showing | Refresh page, verify logged in |
| Theme not changing | Hard refresh (Ctrl+Shift+R) |
| Videos won't play | Use MP4 format or YouTube URL |
| Images won't upload | Try smaller/different format |

---

## **CONTACT & SUPPORT**

📧 For technical issues:
- Check this guide first
- Review browser console (F12)
- Check LocalStorage in DevTools
- Verify data hasn't been cleared

💡 For feature requests:
- Create staff code for new staff
- Add profanity words as needed
- Customize themes in CSS
- Modify code as needed

🔧 For code modifications:
- Use text editor to edit HTML
- Refer to TECHNICAL_DOCUMENTATION.md
- Test thoroughly before deploying
- Keep backup of original

---

**Having issues? Try the solutions above first - 95% of problems are covered here! 🎨**
