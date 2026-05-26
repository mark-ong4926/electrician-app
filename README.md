# Electrician App - Service Provider

Android application สำหรับช่างไฟฟ้า ช่างอ๋องไปครบวงจร

## ⚡ Project Overview

**Electrician App** เป็น Android application ที่ออกแบบมาสำหรับช่างไฟฟ้า เพื่อจัดการงานของตัวเอง ติดตามสถานะงาน และจัดการรายได้

### ✨ Features
- 📋 **Job Management** - จัดการและติดตามสถานะงาน
- 👤 **Service Provider Profile** - จัดการข้อมูลส่วนตัว
- 📱 **Real-time Updates** - อัปเดตสถานะงานแบบ Real-time
- 🔔 **Notifications** - ได้รับแจ้งเตือนจากระบบ

## 🛠️ Tech Stack

- **Language**: Kotlin
- **UI Framework**: Jetpack Compose
- **Backend**: Firebase
  - Firebase Realtime Database
  - Firebase Authentication
  - Firebase Cloud Messaging (FCM)
- **Architecture**: MVVM Pattern
- **Dependency Injection**: Hilt

## 📁 Project Structure

```
electrician-app/
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/electrician/
│   │   │   │   ├── ui/
│   │   │   │   │   ├── screens/
│   │   │   │   │   ├── components/
│   │   │   │   │   └── theme/
│   │   │   │   ├── viewmodel/
│   │   │   │   ├── model/
│   │   │   │   ├── repository/
│   │   │   │   ├── firebase/
│   │   │   │   └── MainActivity.kt
│   │   │   ├── res/
│   │   │   └── AndroidManifest.xml
│   │   ├── test/
│   │   └── androidTest/
│   └── build.gradle.kts
├── build.gradle.kts
├── settings.gradle.kts
└── README.md
```

## 🚀 Getting Started

### Prerequisites
- Android Studio (latest version)
- Android SDK 24+
- Kotlin 1.9+
- Firebase Account

### Installation

1. **Clone Repository**
```bash
git clone https://github.com/mark-ong4926/electrician-app.git
cd electrician-app
```

2. **Setup Firebase**
   - สร้าง Firebase Project ที่ https://console.firebase.google.com
   - ดาวน์โหลด `google-services.json`
   - วางไฟล์ที่ `app/google-services.json`

3. **Open in Android Studio**
   - เปิด Android Studio
   - เลือก "Open an Existing Project"
   - เลือกโฟลเดอร์ `electrician-app`

4. **Build and Run**
```bash
./gradlew build
./gradlew installDebug
```

## 📝 Firebase Setup

### Realtime Database Rules
```json
{
  "rules": {
    "users": {
      "$uid": {
        ".read": "$uid === auth.uid",
        ".write": "$uid === auth.uid"
      }
    },
    "jobs": {
      "$jobId": {
        ".read": "root.child('users').child(auth.uid).exists()",
        ".write": "root.child('users').child(auth.uid).exists()"
      }
    }
  }
}
```

## 📱 App Architecture

### MVVM Pattern
- **Model**: Data models และ Firebase entities
- **View**: Jetpack Compose UI screens
- **ViewModel**: Business logic และ state management

### Data Flow
```
UI (Composable) → ViewModel → Repository → Firebase
```

## 🔐 Authentication

ใช้ Firebase Authentication เพื่อ:
- ลงทะเบียน (Sign Up)
- เข้าสู่ระบบ (Sign In)
- ลืมรหัสผ่าน (Password Reset)

## 📦 Dependencies

```kotlin
// Jetpack Compose
implementation "androidx.compose.ui:ui:1.5.0"
implementation "androidx.compose.material3:material3:1.1.0"

// Firebase
implementation "com.google.firebase:firebase-auth-ktx"
implementation "com.google.firebase:firebase-database-ktx"
implementation "com.google.firebase:firebase-messaging-ktx"

// Hilt
implementation "com.google.dagger:hilt-android:2.46"

// Coroutines
implementation "org.jetbrains.kotlinx:kotlinx-coroutines-android:1.7.1"
```

## 🧪 Testing

```bash
# Run unit tests
./gradlew test

# Run instrumented tests
./gradlew connectedAndroidTest
```

## 📚 Documentation

สำหรับข้อมูลเพิ่มเติม:
- [Android Developer Guide](https://developer.android.com/)
- [Jetpack Compose Documentation](https://developer.android.com/jetpack/compose)
- [Firebase Documentation](https://firebase.google.com/docs)

## 👥 Team

- **Organization**: ช่างอ๋องไปครบวงจร
- **Developer**: mark-ong4926

## 📄 License

MIT License - See LICENSE file for details

## 📞 Support

สำหรับคำถาม หรือปัญหา กรุณาสร้าง Issue ที่ GitHub

---

**Happy Coding! ⚡**
