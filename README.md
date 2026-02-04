# HypeLab Android SDK

Maven repository for the HypeLab Android SDK.

## Installation

### 1. Add the repository

In your project's `settings.gradle.kts`:

```kotlin
dependencyResolutionManagement {
    repositories {
        google()
        mavenCentral()
        maven { url = uri("https://raw.githubusercontent.com/gohypelab/hypelab-sdk-android/v2") }
    }
}
```

Or in `settings.gradle` (Groovy):

```gradle
dependencyResolutionManagement {
    repositories {
        google()
        mavenCentral()
        maven { url 'https://raw.githubusercontent.com/gohypelab/hypelab-sdk-android/v2' }
    }
}
```

### 2. Add the dependency

In your app's `build.gradle.kts`:

```kotlin
dependencies {
    implementation("com.hypelab:hypelab-sdk:1.0.0")
}
```

Or in `build.gradle` (Groovy):

```gradle
dependencies {
    implementation 'com.hypelab:hypelab-sdk:1.0.0'
}
```

## Usage

### Initialize the SDK

```kotlin
import com.hypelab.sdk.HypeLab
import com.hypelab.sdk.Environment

class MyApplication : Application() {
    override fun onCreate() {
        super.onCreate()

        HypeLab.initialize(
            context = this,
            propertySlug = "your-property-slug",
            environment = Environment.PRODUCTION
        )
    }
}
```

### Display a Banner Ad

```kotlin
import com.hypelab.sdk.Banner
import com.hypelab.sdk.BannerSize

val banner = Banner("your-placement-slug", BannerSize.BANNER_320x50)

banner.setListener(object : Banner.Listener {
    override fun onAdLoaded(banner: Banner) {
        bannerContainer.addView(banner.view)
    }
    override fun onAdFailedToLoad(banner: Banner, error: HypeLabError) {
        Log.e("HypeLab", "Failed to load: ${error.message}")
    }
    override fun onAdClicked(banner: Banner) {}
})

banner.load()
```

## Requirements

- Android API 24+ (Android 7.0)
- Kotlin or Java

## Documentation

For full documentation, visit [docs.hypelab.com](https://docs.hypelab.com)
