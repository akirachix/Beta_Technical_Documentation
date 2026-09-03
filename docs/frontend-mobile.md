# Vuka Mobile Application
The mobile implementation of Vuka, allows the users to access the platform from different devices. THis enhances accessibility of the application at any given time.

## Features
The Vuka Mobile Application provides a structured mobile experience that helps users engage with learning, skills development, assessments, progress tracking, and opportunities.

 **Home** <br>
The Home section provides users with an overview of their Vuka experience. <br>
It includes:
  Assessment performance and completed assessments.
  Daily activity and streak tracking.
  Today's learning or content recommendations.
  Quick access to recommended missions.


<div class="feature-card">
<img src="../images/homemobile.png" alt="Vuka Home Dashboard" >
</div>


 **Missions** <br>
The Missions section provides users with and learning content designed to support skill development and continued engagement with the Vuka platform.


<div class="feature-card">
<img src="../images/missionmobile.png" alt="Vuka Home Dashboard" >
</div>


 **Assessments** <br>
The Assessments section allows users to access and complete assessments as part of validating learning from the missions.
Assessment activity contributes to the user's overall assessment performance and helps track completed assessments.


<div class="feature-card">
<img src="../images/assessmetmobile.png" alt="Vuka Home Dashboard" >
</div>

 **Progress** <br>
The Progress section allows users to monitor their scores from the assessments done and enables them to unlock opportunities.


<div class="feature-card">
<img src="../images/progressmobile.png" alt="Vuka Home Dashboard" >
</div>

 **Opportunities** <br>
The Opportunities section connects users with relevant opportunities that can support their transition from learning and skills development toward real-world advancement.


<div class="feature-card">
<img src="../images/opportunitiesmobile.png" alt="Vuka Home Dashboard" >
</div>

 **Settings** <br>
The Settings section provides users with access to application and account-related settings.


<div class="feature-card">
<img src="../images/settingsmobile.png" alt="Vuka Home Dashboard" >
</div>

## Technology Stack
- Flutter - Cross-platform framework used to develop the mobile application
- Dart	- Programming language used for Flutter development
- Android -	Supported mobile platform
- iOS	- Supported mobile platform

## Project Structure
        Beta_Mobile/
        │
        ├── .dart_tool/
        │
        ├── .github/
        │
        ├── vuka/
        │   ├── android/                
        │   ├── assets/                 
        │   ├── ios/                    
        │   ├── lib/                     
        │   ├── linux/                  
        │   ├── macos/                   
        │   ├── test/                    
        │   ├── web/                    
        │   ├── windows/               
        │   │
        │   ├── .gitignore               
        │   ├── .metadata                
        │   ├── analysis_options.yaml    
        │   ├── pubspec.lock            
        │   └── pubspec.yaml             
        │
        ├── .gitignore                   
        ├── README.md                   
        ├── analysis_options.yaml        
        ├── pubspec.lock                
        └── pubspec.yaml                

## Getting Started
Before running the Vuka Mobile Application, make sure you have the following installed: 

- Flutter SDK
- Dart SDK
- Git
- Android Studio 
- An Android emulator or iOS simulator. 
You can verify your Flutter installation by running: 

flutter doctor

**Installation**
```
Clone the repository
git clone https://github.com/akirachix/Beta_Mobile.git

Navigate to the Flutter project <br>
cd Beta_Mobile/vuka

Install Flutter dependencies <br>
flutter pub get

Check the development environment <br>
flutter doctor

Run the application <br>
Connect a physical device or start an emulator, then run: <br>
flutter run
```