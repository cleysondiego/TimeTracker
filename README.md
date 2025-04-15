# ⏱️ TimeTracker

**TimeTracker** is a simple and efficient Kotlin-based SDK for tracking the execution time of code blocks in Android applications. It’s a helpful tool for developers who want to measure performance, analyze bottlenecks, or monitor runtime behavior during development and debugging.

---

## 🚀 Features

- 🔹 Measure start-to-finish execution time for labeled tasks  
- 🔹 Easy-to-use API with minimal setup  
- 🔹 Toggle tracking on/off globally  
- 🔹 Fully customizable logger output

---

## 📦 Installation

### Step 1: Add JitPack to your project

In your root `settings.gradle.kts` or `build.gradle.kts` file:

```kotlin
dependencyResolutionManagement {
    repositories {
        google()
        mavenCentral()
        maven("https://jitpack.io")
    }
}
```

### Step 2: Add the dependency

In your app-level `build.gradle.kts`:

```kotlin
dependencies {
    implementation("com.github.cleysondiego:TimeTracker:<latest-version>")
}
```

Replace `<latest-version>` with the latest [GitHub tag](https://github.com/cleysondiego/TimeTracker/tags).

---

## 🧪 Usage

```kotlin
// Enable or disable tracking globally
TimeTracker.isEnabled = true

// Optionally set a custom logger
TimeTracker.logger = { tag, message ->
    Log.d(tag, message)
}

// Measure how long the screen takes to set up
TimeTracker.measure("MainScreenSetup") {
    setContent {
        TimeTrackerDemoAppTheme {
            Scaffold(modifier = Modifier.fillMaxSize()) { innerPadding ->
                Greeting(
                    name = "Compose",
                    modifier = Modifier.padding(innerPadding)
                )
            }
        }
    }
}

// An alternative way
// Start tracking a labeled operation
TimeTracker.start("loadData")

// Your code block here...

// Stop tracking and log the elapsed time
TimeTracker.stop("loadData")
```

Output:
```
[TimeTracker] MainScreenSetup executed in 2354ms
[TimeTracker] loadData executed in 215ms
```

---

## 📚 Background

This SDK was originally created as a part of an exploration in Android SDK development. The structure and publication process of this library follow the steps described in [this excellent guide on creating and publishing Android SDKs](https://proandroiddev.com/creating-and-publishing-an-android-sdk-a-simple-step-by-step-guide-that-actually-works-3cf3a205f1e4) by Anatolii Frolov.

---

## 📝 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

Feel free to contribute, open issues, or suggest improvements!
