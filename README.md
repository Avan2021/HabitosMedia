# HabitosMedia

# Share Your Spark - Social Wellness App

A social wellness Android app where users can share and view inspirational content through images and short videos.

## Features

- 📸 Upload multiple images and short videos per post
- 🎥 Auto-playing video support
- ❤️ Like posts with animated reactions
- 💬 Comment on posts
- 🔄 Real-time updates using Firestore
- 🎨 Modern Material Design 3 UI with Jetpack Compose

## Required Configuration

### 1. GitHub Setup
1. Create a new GitHub repository
2. Create the following folder structure in your repository:
   ```
   media/
   ├── images/
   └── videos/
   ```
3. Generate a GitHub personal access token:
   - Go to GitHub Settings → Developer Settings → Personal Access Tokens
   - Generate a new token with 'repo' scope
   - Copy the token

4. Open `app/src/main/java/com/example/shareyourspark/data/repository/GitHubRepository.kt`
   and replace these values:
   ```kotlin
   const val GITHUB_TOKEN = "YOUR_GITHUB_TOKEN_HERE"  // Your personal access token
   const val GITHUB_USERNAME = "YOUR_USERNAME_HERE"   // Your GitHub username
   const val GITHUB_REPO = "YOUR_REPO_NAME_HERE"     // Your repository name
   const val GITHUB_BRANCH = "main"                  // Change if using different branch
   ```

### 2. Firebase Setup
1. Create a new Firebase project at [Firebase Console](https://console.firebase.google.com)
2. Add an Android app to your Firebase project:
   - Use package name: `com.example.shareyourspark`
   - Download `google-services.json`
   - Place it in the `app` folder

3. Enable Firestore:
   - Go to Firestore Database in Firebase Console
   - Create database in test mode
   - Set up rules:
   ```javascript
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /{document=**} {
         allow read, write: if true;
       }
     }
   }
   ```

### 3. Required Assets
1. Like Animation:
   - Download a heart/like animation from [LottieFiles](https://lottiefiles.com)
   - Save as `like_animation.json`
   - Place in `app/src/main/res/raw/`

## Project Structure

```
app/
├── build.gradle                 # App-level Gradle config and dependencies
├── src/
│   └── main/
│       ├── java/com/example/shareyourspark/
│       │   ├── data/
│       │   │   ├── models/
│       │   │   │   ├── Post.kt         # Post data model
│       │   │   │   └── Comment.kt      # Comment data model
│       │   │   └── repository/
│       │   │       ├── GitHubRepository.kt    # GitHub media upload (Add your config here)
│       │   │       └── FirestoreRepository.kt  # Firestore operations
│       │   └── ui/
│       │       ├── components/
│       │       │   └── PostCard.kt      # Reusable post component
│       │       └── screens/
│       │           ├── CreatePostScreen.kt  # Post creation screen
│       │           └── FeedScreen.kt        # Main feed screen
│       └── res/
│           └── raw/
│               └── like_animation.json   # Add your Lottie animation here
```

## Quick Start Checklist

✅ Create GitHub repository with media folders  
✅ Add GitHub configuration in `GitHubRepository.kt`  
✅ Set up Firebase project  
✅ Add `google-services.json` to app folder  
✅ Add Lottie animation file  
✅ Build and run!

## Dependencies

- **Jetpack Compose** - Modern UI toolkit
- **Firebase Firestore** - Real-time database
- **ExoPlayer** - Video playback
- **Glide** - Image loading
- **Lottie** - Animations
- **OkHttp** - Networking
- **Kotlin Coroutines** - Asynchronous programming
- **Material Design 3** - UI components and theming

## Contributing

Feel free to submit issues and enhancement requests! 
