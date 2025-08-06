# Dei-Gratcia Hostel Booking System

A modern, secure hostel booking system built with HTML, CSS, JavaScript, and Firebase.

## Features

- **Secure Authentication**: Firebase Authentication for admin access
- **Real-time Database**: Firestore for booking data storage
- **Multi-user Admin Access**: Multiple admins can manage the system
- **Room Management**: Track room availability and bed assignments
- **Booking Management**: Complete booking lifecycle management
- **Student Information**: Detailed student profiles and bed assignments
- **Payment Tracking**: Payment proof upload and verification
- **Responsive Design**: Works on all devices

## Setup Instructions

### 1. Firebase Setup

1. **Create Firebase Project**:
   - Go to [Firebase Console](https://console.firebase.google.com/)
   - Click "Add project"
   - Enter project name (e.g., "dei-gratcia-hostel")
   - Follow the setup wizard

2. **Enable Authentication**:
   - In Firebase Console, go to "Authentication"
   - Click "Get started"
   - Enable "Email/Password" authentication
   - Add your first admin user or use the registration form

3. **Enable Firestore Database**:
   - Go to "Firestore Database"
   - Click "Create database"
   - Choose "Start in test mode" (for development)
   - Select a location close to your users

4. **Get Firebase Config**:
   - Go to Project Settings (gear icon)
   - Scroll down to "Your apps"
   - Click "Add app" → Web app
   - Copy the config object

5. **Update Firebase Config**:
   - Open `index.html`
   - Find the `firebaseConfig` object (around line 3400)
   - Replace the placeholder values with your actual Firebase config:

```javascript
const firebaseConfig = {
    apiKey: "your-actual-api-key",
    authDomain: "your-project.firebaseapp.com",
    projectId: "your-project-id",
    storageBucket: "your-project.appspot.com",
    messagingSenderId: "your-sender-id",
    appId: "your-app-id"
};
```

### 2. Security Rules (Optional but Recommended)

In Firebase Console → Firestore Database → Rules, add these security rules:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Allow read/write for authenticated users only
    match /{document=**} {
      allow read, write: if request.auth != null;
    }
  }
}
```

### 3. Vercel Deployment

1. **Install Vercel CLI**:
   ```bash
   npm install -g vercel
   ```

2. **Deploy to Vercel**:
   ```bash
   # Navigate to your project directory
   cd hostel-main
   
   # Deploy
   vercel
   ```

3. **Follow the prompts**:
   - Link to existing project or create new
   - Confirm deployment settings
   - Wait for deployment to complete

4. **Custom Domain** (Optional):
   - In Vercel dashboard, go to your project
   - Click "Settings" → "Domains"
   - Add your custom domain

## Usage

### For Students:
1. Visit the website
2. Click "Book Now"
3. Fill in personal information
4. Select room type
5. Upload payment proof
6. Submit booking

### For Admins:
1. Click "Admin Login"
2. Register with email/password (first time)
3. Login with credentials
4. Access dashboard to:
   - View all bookings
   - Update booking status
   - Manage rooms
   - View reports

## Room Configuration

The system supports these room types:
- **6 in a Room**: 1 room, 6 beds
- **4 in a Room**: 4 rooms, 16 beds total
- **3 in a Room**: 1 room, 3 beds
- **2 in a Room (Buy Your Own Light)**: 4 buildings, 8 beds total
- **2 in a Room (Prepaid Light)**: 2 rooms, 4 beds total

## Security Features

- **Firebase Authentication**: Secure user management
- **Firestore Security Rules**: Database access control
- **HTTPS Only**: Secure data transmission
- **Input Validation**: Client and server-side validation
- **Activity Logging**: Track all admin actions

## File Structure

```
hostel-main/
├── index.html          # Main application file
├── README.md          # This file
└── .vercelignore      # Vercel deployment config
```

## Troubleshooting

### Common Issues:

1. **Firebase not initialized**:
   - Check your Firebase config
   - Ensure all required Firebase services are enabled

2. **Authentication errors**:
   - Verify email/password authentication is enabled
   - Check if user exists in Firebase Console

3. **Database errors**:
   - Ensure Firestore is created and in test mode
   - Check security rules

4. **Deployment issues**:
   - Verify all files are in the correct directory
   - Check Vercel deployment logs

## Support

For technical support or questions:
- Check Firebase documentation
- Review Vercel deployment guides
- Contact your development team

## License

This project is proprietary software for Dei-Gratcia Hostel. 