# URGENT: Fix Frontend Backend URL

## The Problem
Your frontend is still calling the **OLD** backend URL:
- ❌ Old (being used): `backend-dehn-project-r1541ewf6-rathoryash7s-projects.vercel.app`
- ✅ New (should use): `backend-dehn-project-lcqehwnmx-rathoryash7s-projects.vercel.app`

## Immediate Fix Steps

### Step 1: Verify Frontend Code is Updated
The file `src/config/api.js` should have:
```javascript
return 'https://backend-dehn-project-lcqehwnmx-rathoryash7s-projects.vercel.app/api';
```

### Step 2: Commit and Push Frontend Changes
```bash
cd ../denn_project
git add src/config/api.js
git commit -m "Update backend URL to new deployment"
git push
```

### Step 3: Wait for Vercel to Redeploy
1. Go to Vercel Dashboard
2. Check your frontend project
3. Wait for the new deployment to complete (usually 1-2 minutes)
4. The new deployment will use the updated backend URL

### Step 4: Clear Browser Cache
After redeployment:
1. Hard refresh the page: `Ctrl+Shift+R` (Windows) or `Cmd+Shift+R` (Mac)
2. Or open in incognito/private window
3. Check browser console - should now show the NEW backend URL

## Verify It's Fixed

After redeployment, check browser console:
```javascript
// Should show the NEW URL
console.log('API URL:', 'https://backend-dehn-project-lcqehwnmx-rathoryash7s-projects.vercel.app/api');
```

## If Still Not Working

### Option 1: Force Rebuild in Vercel
1. Vercel Dashboard → Your Frontend Project
2. Go to Deployments
3. Click "..." on latest deployment
4. Click "Redeploy"

### Option 2: Check Build Logs
1. Vercel Dashboard → Frontend Project → Deployments
2. Click on the latest deployment
3. Check "Build Logs" for any errors
4. Make sure the build completed successfully

### Option 3: Verify File Was Saved
1. Open `src/config/api.js` in your editor
2. Make sure line 9 shows: `return 'https://backend-dehn-project-lcqehwnmx-rathoryash7s-projects.vercel.app/api';`
3. If not, update it and save
4. Commit and push again

## Quick Test

After redeployment, open browser console and run:
```javascript
fetch('https://backend-dehn-project-lcqehwnmx-rathoryash7s-projects.vercel.app/api/test')
  .then(r => r.json())
  .then(console.log)
  .catch(console.error);
```

Should return: `{success: true, message: "Backend is accessible", ...}`

