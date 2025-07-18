# Firebase Authentication Setup Guide

## Steps to Complete Firebase Setup:

### 1. Add Web App to Firebase Project
1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Select your project: `fraudguardai-627dc`
3. Go to **Project Settings** (gear icon)
4. Scroll down to "Your apps" section
5. Click **Add app** → **Web** (`</>` icon)
6. Register your app:
   - App nickname: `FraudGuard AI Web`
   - Check "Also set up Firebase Hosting" (optional)
7. Click **Register app**
8. **Copy the config object** and update `src/lib/firebase.ts`

### 2. Enable Authentication
1. In Firebase Console, go to **Authentication**
2. Click **Get started** if not already set up
3. Go to **Sign-in method** tab
4. Enable **Email/Password** provider:
   - Click on Email/Password
   - Toggle **Enable**
   - Click **Save**

### 3. Update Firebase Configuration
Replace the config in `src/lib/firebase.ts` with the actual config from Firebase:

```typescript
const firebaseConfig = {
  apiKey: "YOUR_ACTUAL_API_KEY",
  authDomain: "fraudguardai-627dc.firebaseapp.com",
  projectId: "fraudguardai-627dc",
  storageBucket: "fraudguardai-627dc.appspot.com",
  messagingSenderId: "733636033322",
  appId: "YOUR_ACTUAL_APP_ID"
};
```

### 4. Test Authentication
1. Go to `http://localhost:8081/register`
2. Create a new account
3. Check Firebase Console → Authentication → Users to see the new user
4. Try logging in with the created account

## Current Status:
- ✅ Firebase project created
- ✅ Project ID configured
- ✅ API Key configured
- ⏳ Need to add Web App and get proper App ID
- ⏳ Need to enable Email/Password authentication

## After Setup:
Your dashboard will show user-specific information from Firebase Auth:
- User email from Firebase
- User display name (if set)
- Proper authentication protection
- Secure logout functionality
