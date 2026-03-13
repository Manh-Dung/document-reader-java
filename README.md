# Document Reader (Android)

A powerful, standalone Android library for rendering and viewing multiple document formats directly within your app, without requiring external office applications.

## ✨ Features

* **Wide Format Support:**
  * **Word:** `.doc`, `.docx`, `.dot`, `.dotx`, `.dotm`
  * **Excel:** `.xls`, `.xlsx`, `.xlt`, `.xltx`, `.xltm`, `.xlsm`, `.csv`
  * **PowerPoint:** `.ppt`, `.pptx`, `.pot`, `.potx`, `.potm`, `.pptm`
  * **PDF:** `.pdf`
  * **Text/Others:** `.txt`, `.rtf`, `.html`, `.xml`, `.json`
* **Easy Integration:** Launch the document viewer instantly using standard Android Intents.
* **Self-Contained:** Comes with built-in UI for document browsing, zooming, and pagination.
* **Flutter Compatible:** Can be easily integrated into Flutter apps using Platform Views (see repository examples).

---

## 🚀 Installation (Gradle)

**Step 1: Add the JitPack repository**  
Add the `jitpack.io` URL to your root `settings.gradle` (or `settings.gradle.kts`):

```gradle
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        google()
        mavenCentral()
        maven { url 'https://jitpack.io' } // <-- Add this line
    }
}
```

*(If your project is older and uses root `build.gradle`, add it inside `allprojects { repositories { ... } }`)*

**Step 2: Add the library dependency**  
In your app-level `build.gradle` (or `build.gradle.kts`), add:

```gradle
dependencies {
    implementation 'com.github.Manh-Dung:document-reader-java:1.0.1'
}
```

**Step 3: Exclude conflicting META-INF files**  
Office parsing libraries often introduce duplicate dependencies. To avoid build errors, add exclusions in your app-level `build.gradle` inside the `android {}` block:

```gradle
android {
    ...
    packagingOptions {
        exclude 'META-INF/DEPENDENCIES'
        exclude 'META-INF/INDEX.LIST'
        exclude 'META-INF/LICENSE'
        exclude 'META-INF/NOTICE'
    }
}
```

**(Optional) Enable Jetifier**  
If you face AndroidX compatibility issues, ensure this is in your `gradle.properties`:
```properties
android.enableJetifier=true
```

---

## 💻 Usage

Opening a document is as simple as passing the **absolute file path** via an Intent to `All_Document_Reader_Activity`. 

### Kotlin
```kotlin
import com.ahmadullahpk.alldocumentreader.activity.All_Document_Reader_Activity

val filePath = "/storage/emulated/0/Download/sample.pdf" // Example absolute path

val intent = Intent(this, All_Document_Reader_Activity::class.java).apply {
    putExtra("path", filePath)
    putExtra("fromAppActivity", true)
}
startActivity(intent)
```

### Java
```java
import com.ahmadullahpk.alldocumentreader.activity.All_Document_Reader_Activity;

String filePath = "/storage/emulated/0/Download/sample.pdf"; // Example absolute path

Intent intent = new Intent(this, All_Document_Reader_Activity.class);
intent.putExtra("path", filePath);
intent.putExtra("fromAppActivity", true);
startActivity(intent);
```

### Important Note on Permissions
Ensure your app has requested the necessary storage permissions (`READ_EXTERNAL_STORAGE` or MANAGE_EXTERNAL_STORAGE on newer Android versions) before attempting to open files from the device storage.

---

### Contact & Support
If you encounter any issues or have feature requests, please open an issue on the GitHub repository.
