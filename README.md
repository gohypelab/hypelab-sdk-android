# HypeLab SDK for Android

Integrate HypeLab ads in your Android app.

## Getting Started

### Install HypeLab SDK

Add the GitHub repository to your project.

Kotlin:

```kotlin
dependencyResolutionManagement {
  repositories {
    // ...
    maven { url = uri("https://raw.githubusercontent.com/gohypelab/hypelab-sdk-android/master/") }
  }
}
```

Groovy:

```groovy
dependencyResolutionManagement {
	repositories {
    // ...
		maven { url 'https://raw.githubusercontent.com/gohypelab/hypelab-sdk-android/master/' }
	}
}
```

Then add the `hypelab-sdk` dependency to your project.

Kotlin:

```kotlin
dependencies {
  implementation("com.hypelab:hypelab-sdk:1.0.0")
}
```

Groovy:

```groovy
dependencies {
  implementation 'com.hypelab:hypelab-sdk:1.0.0'
}
```

### Configure HypeLab SDK

Kotlin:

```kotlin
import com.hypelab.hypelab_sdk.HypeLab
import com.hypelab.hypelab_sdk.Config

// ...

val config = Config("environment", "propertySlug")
HypeLab.initialize(config)
```

Java:

```java
import com.hypelab.hypelab_sdk.HypeLab;
import com.hypelab.hypelab_sdk.Config;

// ...

Config config = new Config("environment", "propertySlug");
HypeLab.initialize(config);
```

### Create a Rewarded ad

Kotlin:

```kotlin
import com.hypelab.hypelab_sdk.Rewarded

// ...

val rewarded = Rewarded("placementSlug");
rewarded.onReady = { Log.d("MyApp", "Rewarded onReady") }
rewarded.onError = { Log.d("MyApp", "Rewarded onError") }
rewarded.onVideoStart = { Log.d("MyApp", "Rewarded onVideoStart") }
rewarded.onVideoComplete = { Log.d("MyApp", "Rewarded onVideoComplete") }
rewarded.onVideoError = { Log.d("MyApp", "Rewarded onVideoError") }
rewarded.onImpression = { Log.d("MyApp", "Rewarded onImpression") }
rewarded.onClick = { Log.d("MyApp", "Rewarded onClick") }
```

Java:

```java
import com.hypelab.hypelab_sdk.Rewarded;

// ...

Rewarded rewarded = new Rewarded("placementSlug");
rewarded.onReady = () -> Log.d("MyApp", "Rewarded onReady");
rewarded.onError = () -> Log.d("MyApp", "Rewarded onError");
rewarded.onVideoStart = () -> Log.d("MyApp", "Rewarded onVideoStart");
rewarded.onVideoComplete = () -> Log.d("MyApp", "Rewarded onVideoComplete");
rewarded.onVideoError = () -> Log.d("MyApp", "Rewarded onVideoError");
rewarded.onImpression = () -> Log.d("MyApp", "Rewarded onImpression");
rewarded.onClick = () -> Log.d("MyApp", "Rewarded onClick");
```

### Show a Rewarded ad

Kotlin:

```kotlin
rewarded.show()
```

Java:

```java
rewarded.show();
```
