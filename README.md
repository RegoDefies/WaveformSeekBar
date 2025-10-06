# WaveformSeekBar

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![JitPack](https://jitpack.io/v/RegoDefies/WaveformSeekBar.svg)](https://jitpack.io/#RegoDefies/WaveformSeekBar)
![Android 15+](https://img.shields.io/badge/API-36%2B-blue)
![Alignment](https://img.shields.io/badge/16KB-ready-success)
![Language](https://img.shields.io/badge/Kotlin-1.9.25-9cf)
![Gradle](https://img.shields.io/badge/Gradle-8.7-brightgreen)

# WaveformSeekBar
**Enhanced audio waveform visualization and seek bar for Android**

This repository provides a modernized version of the [WaveformSeekBar](https://github.com/massoudss/waveformSeekBar) library — rebuilt and optimized for **Android 15+ (API 36)** and devices using **16 KB memory pages**.  

It powers the waveform playback interface in apps such as [**Resus**](https://resusapp.com), a real-time medical simulation and training platform.

---

## ✨ Key Improvements

| Feature | Description |
|----------|--------------|
| 🧠 **Android 15+ Ready** | Compiled with `compileSdk 36` and aligned to Google’s 16 KB standard |
| ⚙️ **Updated Amplituda Core** | Integrated Amplituda **v2.3.1**, rebuilt with FFmpeg 7.1 |
| 🧱 **Modern Build Stack** | Kotlin 1.9.25 • Gradle 8.7 • Java 21 |
| 🧩 **Dependency Isolation** | The Amplituda dependency is bundled — no manual addition required |
| 🚀 **Backward Compatible** | Works on all devices from **API 24+** |
| 🎵 **Improved Stability** | Smoother rendering and optimized memory management for long waveforms |

---

## 📸 Examples & Screenshots

| Default Waveform | Waveform with Markers | Animated Playback |
|------------------|----------------------|-------------------|
| <img src="https://github.com/user-attachments/assets/ac09e7e4-1999-435c-8fef-dd93ff68e499" width="400"/> | <img src="https://github.com/user-attachments/assets/e8686f4a-3568-4574-883a-e24c1c018e78" width="400"/> | <img src="https://github.com/user-attachments/assets/dfd7282d-e582-4637-ae2f-7a632f885318" width="300"/> |

---

## 📦 Installation

### 1️⃣ Add the JitPack repository

In your **`settings.gradle`**:

```gradle
dependencyResolutionManagement {
    repositories {
        google()
        mavenCentral()
        maven(url = "https://jitpack.io")
    }
}
```

### 2️⃣ Add the dependency

In your **`app/build.gradle`**:

```gradle
dependencies {
    implementation("com.github.rego-defies:WaveformSeekBar:5.1.3")
}
```

> 💡 You don’t need to manually include Amplituda — it’s already included.

---

## 🧩 Basic Usage

### XML Example

```xml
<com.masoudss.lib.WaveformSeekBar
    android:id="@+id/waveformSeekBar"
    android:layout_width="match_parent"
    android:layout_height="80dp"
    app:wave_progress="25"
    app:wave_max_progress="100"
    app:wave_background_color="@color/gray"
    app:wave_progress_color="@color/cyan"
    app:wave_corner_radius="2dp"
    app:wave_gravity="center" />
```

### Kotlin Example

```kotlin
// Load waveform from local file
waveformSeekBar.setSampleFrom(File("/storage/emulated/0/Music/song.mp3"))

// Observe progress
waveformSeekBar.onProgressChanged = object : SeekBarOnProgressChanged {
    override fun onProgressChanged(
        waveformSeekBar: WaveformSeekBar,
        progress: Int,
        fromUser: Boolean
    ) {
        Log.d("Waveform", "Progress: $progress")
    }
}
```

---

## 🎛️ Advanced Features

### 📍 Add Markers

```kotlin
val markers = hashMapOf<Float, String>()
markers[waveformSeekBar.maxProgress / 2] = "Midpoint"
markers[10f] = "Intro"
waveformSeekBar.setMarker(markers)
```

### 🎚️ Load Waveform from Various Sources

| Source | Example |
|--------|----------|
| File | `waveformSeekBar.setSampleFrom(File("/storage/.../song.mp3"))` |
| Path | `waveformSeekBar.setSampleFrom("/storage/.../song.mp3")` |
| URL | `waveformSeekBar.setSampleFrom("https://example.com/song.mp3")` |
| Uri | `waveformSeekBar.setSampleFrom(uri)` |
| Resource | `waveformSeekBar.setSampleFrom(R.raw.song)` |
| Custom IntArray | `waveformSeekBar.setSampleFrom(intArrayOf(1,2,3,4))` |

---

## 🎨 Customization Settings

| Attribute | Type | Kotlin | Description |
|------------|------|---------|-------------|
| `wave_progress` | Float | `progress` | Current progress value |
| `wave_max_progress` | Float | `maxProgress` | Maximum progress value |
| `wave_visible_progress` | Float | `visibleProgress` | Visible section of waveform |
| `wave_width` | Dimension | `waveWidth` | Width of each bar |
| `wave_gap` | Dimension | `waveGap` | Spacing between bars |
| `wave_min_height` | Dimension | `waveMinHeight` | Minimum bar height |
| `wave_corner_radius` | Dimension | `waveCornerRadius` | Rounded bar corners |
| `wave_background_color` | Color | `waveBackgroundColor` | Inactive wave color |
| `wave_progress_color` | Color | `waveProgressColor` | Active wave color |
| `marker_color` | Color | `markerColor` | Marker line color |
| `marker_text_color` | Color | `markerTextColor` | Marker label color |
| `marker_text_size` | Dimension | `markerTextSize` | Label text size |
| `marker_text_padding` | Dimension | `markerTextPadding` | Label padding |

---

## ⚡ Performance Optimization

To reduce APK size and improve runtime performance, add this flag to your `AndroidManifest.xml`:

```xml
<application
    ...
    android:extractNativeLibs="false">
</application>
```

This prevents unnecessary extraction of native Amplituda libraries.

---

## 🧪 Version Compatibility Matrix

| WaveformSeekBar | Amplituda | Android API | Notes |
|------------------|------------|--------------|--------|
| 5.1.3 | 2.3.1 | 24–36 | 16 KB page size compliant |
| 5.0.2 | 2.2.2 | 21–33 | Legacy version (deprecated) |

---

## 🧰 Technical Details

- **Language:** Kotlin  
- **Build system:** Gradle 8.7  
- **Java compatibility:** 21  
- **Min SDK:** 24  
- **Target SDK:** 36  

---

## 🧾 License

```
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at:

    http://www.apache.org/licenses/LICENSE-2.0
```

---

## 🧭 Acknowledgements

- Original work by [@massoudss](https://github.com/massoudss)
- Rebuilt and maintained by [Rego Defies](https://github.com/rego-defies)
- Special thanks to [Amplituda](https://github.com/lincollincol/Amplituda) for the decoding core

---

## 🩺 Used in Production

The **Resus** app — a real-time medical simulation tool — uses this library to render dynamic waveforms for training scenarios in cardiology and emergency care.

[➡️ Learn more about Resus](https://play.google.com/store/apps/details?id=com.quantingo.resus)
