# 🩸 CycleTrack — Menstrual Cycle & Health Tracking App

**Android application for cycle prediction, symptom logging, and health tracking with partner sharing and subscription features.**

<div align="center">

[![Android](https://img.shields.io/badge/Android-26+-green?logo=android)](https://developer.android.com/)
[![Kotlin](https://img.shields.io/badge/Kotlin-1.9.22-purple?logo=kotlin)](https://kotlinlang.org/)
[![License](https://img.shields.io/badge/License-MIT-blue)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Production%20Ready-brightgreen)]()

**[Features](#-features) • [Architecture](#-architecture) • [Setup](#-setup) • [Development](#-development) • [Roadmap](#-roadmap)**

</div>

---

## 📱 Features

### Core Features (MVP)
- 🔄 **Menstrual Cycle Tracking** — Log period start/end dates and calculate cycle patterns
- 📊 **Cycle Predictions** — Automatic prediction of next period, ovulation, and fertile window
- 🩹 **Symptom Logging** — Track symptoms (cramps, mood, energy, etc.) with severity levels
- 📈 **Cycle Analytics** — View cycle statistics, regularity, and health insights
- 🎨 **Phase Indicators** — Color-coded cycle phases (Menstrual, Follicular, Ovulation, Luteal)

### Premium Features
- 👥 **Partner Mode** — Share cycle data with partner for collaborative planning
- 🤰 **Pregnancy Mode** — Track pregnancy milestones and due date
- 📤 **Data Export** — Export cycle data as CSV or PDF for medical consultations
- 🏥 **Health Connect Integration** — Sync steps, heart rate, temperature from device health data

### Additional
- 🔐 **Local-First Storage** — All data stored locally on device (Realm database)
- 🌙 **Dark Mode** — Full dark/light theme support
- 🌍 **Português Brasileiro** — Complete Portuguese UI
- 📱 **Material 3 Design** — Modern, responsive Jetpack Compose UI

---

## 🏗️ Architecture

### Clean Architecture
```
┌─────────────────────────────────────┐
│    Presentation Layer               │
│  (Composables + ViewModels)         │
├─────────────────────────────────────┤
│    Domain Layer                     │
│  (Use Cases + Models)               │
├─────────────────────────────────────┤
│    Data Layer                       │
│  (Repositories + DAOs)              │
├─────────────────────────────────────┤
│    Infrastructure Layer             │
│  (Realm + Hilt DI)                  │
└─────────────────────────────────────┘
```

### Tech Stack
- **Language:** Kotlin 1.9.22
- **UI Framework:** Jetpack Compose + Material 3
- **Architecture:** Clean Architecture + MVVM
- **Dependency Injection:** Hilt
- **Database:** Realm (primary) + Room (analytics)
- **Networking:** Retrofit + OkHttp
- **Serialization:** Moshi + kotlinx.serialization
- **Health Integration:** Health Connect API
- **Error Tracking:** Sentry
- **State Management:** StateFlow + ViewModel
- **Build System:** Gradle 8.7+

---

## 🚀 Getting Started

### Prerequisites
- Java 17 (JVM target)
- Android SDK 35
- Gradle 8.7+
- Kotlin Plugin 1.9.22
- Android Studio 2024.1.1+ (recommended)

### Build & Run

```bash
# Clone repository
git clone https://github.com/iancodeco/cycletrack-app.git
cd cycletrack-app

# Clean build
./gradlew clean

# Build debug APK
./gradlew assembleDebug

# Run on emulator/device
./gradlew installDebug

# Run all checks (lint, tests, build)
./gradlew build

# Format code
./gradlew ktlintFormat

# Static analysis
./gradlew detekt
```

### Individual Tasks
```bash
# Lint & Analysis
./gradlew detekt            # Detekt static analysis
./gradlew ktlintCheck       # Code style validation
./gradlew ktlintFormat      # Auto-fix code style

# Testing
./gradlew testDebugUnitTest # Unit tests only
./gradlew connectedDebugAndroidTest  # Instrumented tests

# Build variants
./gradlew bundleRelease     # Release AAB (requires keystore)
./gradlew assembleDebug     # Debug APK
```

---

## 📂 Project Structure

```
cycletrack-app/
├── app/src/
│   ├── main/
│   │   ├── java/com/seuapp/cycletrack/
│   │   │   ├── domain/                  # Domain layer (use cases + models)
│   │   │   │   ├── model/              # Cycle, Symptom, Prediction, UserProfile, Pregnancy
│   │   │   │   ├── repository/         # 11 repository interfaces
│   │   │   │   └── usecase/            # 9 business logic use cases
│   │   │   ├── data/                    # Data layer (repositories + DAOs)
│   │   │   │   ├── repository/         # 11 repository implementations
│   │   │   │   ├── local/
│   │   │   │   │   ├── realm/
│   │   │   │   │   │   ├── entities/   # 11 Realm objects
│   │   │   │   │   │   └── dao/        # 11 DAOs
│   │   │   │   │   └── mapper/         # Domain ↔ Realm converters
│   │   │   │   └── di/                 # Hilt modules (3 total)
│   │   │   ├── presentation/            # Presentation layer (Compose + ViewModel)
│   │   │   │   ├── ui/
│   │   │   │   │   ├── home/           # HomeScreen
│   │   │   │   │   ├── calendar/       # CalendarScreen
│   │   │   │   │   ├── logging/        # LoggingScreen
│   │   │   │   │   ├── insights/       # InsightsScreen
│   │   │   │   │   ├── profile/        # ProfileScreen
│   │   │   │   │   ├── onboarding/     # OnboardingScreen
│   │   │   │   │   └── theme/          # Design system + Material 3 theme
│   │   │   │   └── viewmodel/          # 11 ViewModels (@HiltViewModel)
│   │   │   └── util/                    # Utilities, logging, constants
│   │   ├── res/                         # Resources (strings, colors, drawables)
│   │   └── AndroidManifest.xml
│   ├── test/                            # Unit tests (JUnit 4/5, Mockito)
│   └── androidTest/                     # Instrumented tests (Espresso, Compose)
├── CLAUDE.md                            # Project guidelines & conventions
├── build.gradle.kts                     # Build configuration
├── gradle.properties                    # Feature flags & build settings
└── README.md                            # This file
```

---

## 🎯 Development Phases

### ✅ Phase 1: Foundation (Complete)
- Hilt DI setup
- Realm database initialization
- Core infrastructure

### ✅ Phase 2: Architecture (Complete)
- 11 Repositories (Cycle, Symptom, Prediction, UserProfile, Pregnancy, Partner, Subscription, Content, HealthDataPoint, Notification, Export)
- 11 ViewModels with StateFlow state management
- 7 Composable screens refactored

### ✅ Phase 3: Business Logic (Complete)
- 9 Use Cases (cycle calculations, predictions, stats, symptom tracking)
- Use case integration into ViewModels
- HomeScreen with real calculated values
- DemoStore removal (clean architecture)

### ⏳ Phase 4: Backend Integration (Next)
- Firebase Authentication
- Firestore sync (optional)
- Partner sharing
- Push notifications

### ⏳ Phase 5: Advanced Features
- Health Connect integration
- Pregnancy mode
- Export (CSV/PDF)
- Anonymous mode

### ⏳ Phase 6: Polish & Release
- UI/UX refinement
- Performance optimization
- Testing & QA
- Play Store release

---

## 🔧 Configuration

### Feature Flags (gradle.properties)
```properties
feature.healthConnect.enabled=true
feature.partnerMode.enabled=true
feature.pregnancyMode.enabled=true
feature.perimenopauseMode.enabled=true
feature.anonymousMode.enabled=true
feature.export.enabled=true
feature.biometricAuth.enabled=true
```

### Key Files
- `CLAUDE.md` — Project guidelines, patterns, testing strategy
- `gradle.properties` — Build configuration, feature flags, Gradle settings
- `.editorconfig` — Code style (4 spaces, 120 char limit)
- `detekt.yml` — Static analysis rules
- `ktlint.yml` — Code formatting rules

---

## 🧪 Testing

### Unit Tests
```bash
./gradlew testDebugUnitTest
```
- Location: `src/test/java/`
- Framework: JUnit 4 + Mockito
- Coverage: Domain logic, repositories, ViewModels

### Instrumented Tests
```bash
./gradlew connectedDebugAndroidTest
```
- Location: `src/androidTest/java/`
- Framework: Espresso + Compose UI test APIs
- Coverage: Navigation, screen interactions, edge cases
- Requires: Running emulator/device

### Lint & Analysis
```bash
./gradlew detekt        # Detekt rules
./gradlew ktlintCheck   # Code formatting
```

---

## 📚 Code Conventions

### Naming
- **Classes:** PascalCase (`HomeViewModel`, `CycleRepository`)
- **Functions/Properties:** camelCase (`loadCycles()`, `currentCycle`)
- **Constants:** UPPER_CASE (`DB_VERSION`)
- **Composables:** PascalCase (`HomeScreen()`, `CycleRing()`)

### Imports
- No wildcard imports (enforced by ktlint)
- Exceptions: `kotlinx.coroutines.*`, `androidx.compose.*`
- Remove unused imports regularly

### Architecture Patterns
1. **Repository Pattern:** Interfaces in domain/, implementations in data/
2. **ViewModel Pattern:** @HiltViewModel with StateFlow for state
3. **Mapper Pattern:** Domain ↔ Realm conversions
4. **Use Case Pattern:** Business logic as suspend functions with operator overload

### Logging
```kotlin
// ✅ Correct
Timber.d("Debug: %s", value)
Timber.e(exception, "Error occurred")

// ❌ Incorrect
println("Debug message")
Log.d("TAG", "Debug")
```

### Database
```kotlin
// ✅ Realm transactions
realm.write {
    copyToRealm(cycleData)
    copyToRealm(predictionData)
}

// ✅ Coroutine safety
withContext(Dispatchers.IO) {
    // DB operations
}
```

---

## 🔐 Privacy & Security

- **Data Storage:** All data stored locally on device (no cloud by default)
- **Privacy Policy:** LGPD/GDPR/CCPA compliant (see `docs/legal/`)
- **Health Data:** Optional Health Connect integration requires explicit consent
- **No Tracking:** No analytics or tracking by default (Firebase optional)

---

## 📖 Documentation

| File | Purpose |
|------|---------|
| `CLAUDE.md` | Project guidelines, architecture patterns, testing strategy |
| `docs/design-system.md` | Component mappings, colors, typography |
| `docs/infrastructure-setup.md` | Firebase, Play Console, Sentry setup |
| `docs/legal/` | Privacy policy, Terms of Service |
| `PHASE2_COMPLETE.md` | Phase 2 architecture details |
| `PHASE3_FINAL.md` | Phase 3 use cases & integration |

---

## 🤝 Contributing

### Workflow
1. Create feature branch: `git checkout -b feature/my-feature`
2. Make changes following code conventions
3. Run checks: `./gradlew build`
4. Format code: `./gradlew ktlintFormat`
5. Commit with conventional messages: `feat(domain): add new feature`
6. Push and create pull request

### Commit Messages
```
feat(area): description      # New feature
fix(area): description       # Bug fix
refactor(area): description  # Code refactoring
chore(area): description     # Build, CI, dependencies
docs(area): description      # Documentation
test(area): description      # Tests
```

---

## 📋 Requirements

### Minimum SDK
- **Target:** Android 35
- **Minimum:** Android 26 (Android 8.0)
- **Reason:** Health Connect API requirement

### Device Requirements
- 100 MB free storage
- 2 GB RAM minimum
- Biometric sensor (optional, for biometric auth)

---

## 🐛 Known Issues & Limitations

- GetCycleStatsUseCase not yet shown in UI (planned for Phase 3.5)
- Partner sharing UI stubs (backend pending)
- Health Connect integration pending (Phase 5)
- Pregnancy mode UI placeholder (Phase 5)

---

## 📅 Roadmap

### Q1 2026
- [x] Phase 1-3: Foundation + Architecture + Use Cases
- [ ] Phase 4: Backend Integration (Firebase Auth, Firestore)
- [ ] Phase 5: Advanced Features (Health Connect, Pregnancy Mode)

### Q2 2026
- [ ] Phase 6: Polish & Release
- [ ] Play Store launch
- [ ] Marketing & user acquisition

### Q3-Q4 2026
- [ ] Community features (chat with partner)
- [ ] Medical integrations (export to doctors)
- [ ] Advanced analytics & insights

---

## 📧 Support

**Issues:** Report bugs via GitHub Issues  
**Questions:** Discuss in GitHub Discussions  
**Email:** contact@cycletrack.app (future)

---

## 📄 License

MIT License — See [LICENSE](LICENSE) file for details

---

## 🙏 Acknowledgments

- **Jetpack Compose** team for amazing UI framework
- **Realm** for local database solution
- **Hilt** for dependency injection
- **Material 3** for design system

---

<div align="center">

**Made with ❤️ for menstrual health tracking**

[GitHub](https://github.com/iancodeco/cycletrack-app) • [Issues](https://github.com/iancodeco/cycletrack-app/issues) • [Discussions](https://github.com/iancodeco/cycletrack-app/discussions)

</div>
