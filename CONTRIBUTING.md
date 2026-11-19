# Contributing to CycleTrack

Thank you for your interest in contributing to CycleTrack! This document provides guidelines and instructions for contributing.

## Code of Conduct

- Be respectful and inclusive
- Welcome diverse perspectives
- Focus on the code, not the person
- Help others learn and grow

## Getting Started

### 1. Fork & Clone
```bash
git clone https://github.com/YOUR_USERNAME/cycletrack-app.git
cd cycletrack-app
git remote add upstream https://github.com/iancodeco/cycletrack-app.git
```

### 2. Create Feature Branch
```bash
git checkout -b feature/your-feature-name
```

### 3. Set Up Development Environment
```bash
# Install dependencies
./gradlew build

# Format code
./gradlew ktlintFormat

# Run checks
./gradlew detekt
```

## Development Workflow

### Code Style
- **Language:** Kotlin 1.9.22
- **Indentation:** 4 spaces
- **Line length:** 120 characters max
- **Format:** `./gradlew ktlintFormat` auto-fixes most issues

### Architecture
Follow Clean Architecture patterns:
- **Domain:** Use cases, models, repository interfaces
- **Data:** Repository implementations, DAOs, mappers
- **Presentation:** ViewModels, Composables

### Commit Messages
```
feat(area): short description     # New feature
fix(area): short description      # Bug fix
refactor(area): short description # Code refactoring
test(area): short description     # Tests
docs(area): short description     # Documentation
chore(area): short description    # Build, CI, dependencies
```

Examples:
```
feat(cycle): add cycle phase calculation use case
fix(home): correct fertile window date display
test(repository): add cycle repository tests
docs(readme): update setup instructions
```

### Testing

Write tests for:
- Use cases (domain logic)
- Repositories (data access)
- ViewModels (state management)

```bash
# Unit tests
./gradlew testDebugUnitTest

# Instrumented tests
./gradlew connectedDebugAndroidTest
```

### Lint & Analysis

Before pushing, run:
```bash
# Code formatting
./gradlew ktlintFormat

# Static analysis
./gradlew detekt

# Full build
./gradlew build
```

## Pull Request Process

### Before Creating PR
1. ✅ Code formatted: `./gradlew ktlintFormat`
2. ✅ Lint passes: `./gradlew detekt`
3. ✅ Tests pass: `./gradlew testDebugUnitTest`
4. ✅ Full build succeeds: `./gradlew build`
5. ✅ Branch up-to-date with main: `git rebase upstream/main`

### Creating PR
1. Push to your fork: `git push origin feature/your-feature`
2. Open PR on GitHub
3. Use PR template (auto-filled)
4. Link related issues: `Closes #123`

### PR Description Template
```markdown
## Summary
Brief description of what this PR does

## Changes
- Change 1
- Change 2
- Change 3

## Testing
- [ ] Unit tests added/updated
- [ ] Manual testing performed
- [ ] Tested on device

## Checklist
- [ ] Code formatted with ktlintFormat
- [ ] No lint warnings (detekt clean)
- [ ] All tests pass
- [ ] No breaking changes
```

### Review Process
- At least 1 approval required
- All comments addressed
- CI pipeline passes
- Squash commits when merging

## Areas to Contribute

### High Priority
- 🔧 Backend integration (Firebase Auth, Firestore)
- 🧪 Unit tests for use cases
- 📱 UI/UX improvements
- 🐛 Bug fixes

### Medium Priority
- 📚 Documentation improvements
- ♿ Accessibility enhancements
- 🌍 Localization (more languages)
- 📊 Analytics & insights

### Low Priority
- 💡 Code refactoring
- ⚡ Performance optimization
- 🎨 Design system updates
- 🔧 Build system improvements

## Development Phases

Current focus: **Phase 4 — Backend Integration**

See [README.md](README.md) for phase descriptions and roadmap.

## Reporting Issues

### Bug Reports
Include:
- **Device:** Model, Android version
- **Steps:** How to reproduce
- **Expected:** What should happen
- **Actual:** What happens instead
- **Logs:** Android Studio logcat output

### Feature Requests
Include:
- **Description:** What feature
- **Use case:** Why needed
- **Benefits:** What improves
- **Mockups:** Screenshots/designs (optional)

## Git Workflow

### Normal Flow
```bash
# 1. Update your branch
git fetch upstream
git rebase upstream/main

# 2. Make changes
git add path/to/file.kt
git commit -m "feat(area): description"

# 3. Push to your fork
git push origin feature/your-feature

# 4. Create PR on GitHub
# (Fill in template)

# 5. Address feedback
git add .
git commit -m "refactor: address review comments"
git push origin feature/your-feature
```

### Branch Naming
```
feature/feature-name       # New feature
fix/bug-name              # Bug fix
refactor/refactor-name    # Code refactoring
test/test-name            # Test additions
docs/doc-name             # Documentation
```

## Code Review Checklist

Reviewers check for:
- ✅ Code style (follows conventions)
- ✅ Architecture (follows Clean Architecture)
- ✅ Testing (adequate test coverage)
- ✅ Documentation (clear comments, updated docs)
- ✅ Performance (no obvious inefficiencies)
- ✅ Security (no vulnerabilities)
- ✅ Functionality (works as intended)

## Resources

- [Kotlin Documentation](https://kotlinlang.org/docs/home.html)
- [Jetpack Compose Docs](https://developer.android.com/compose)
- [Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)
- [Hilt Dependency Injection](https://dagger.dev/hilt/)
- [Realm Documentation](https://www.mongodb.com/docs/realm/sdk/kotlin/)
- [Android Best Practices](https://developer.android.com/guide)

## Questions?

- **GitHub Issues:** Technical questions, bug reports
- **GitHub Discussions:** General questions, ideas
- **Email:** contact@cycletrack.app (future)

---

**Thank you for contributing to CycleTrack! 🩸**
