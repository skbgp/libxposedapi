
# Xposed API Setup Guide

This project uses the **Xposed API** as a compile-only dependency.
Because the API is not available on Maven Central, you must add the `.jar` files manually.

Follow the steps below to configure your project correctly.

---

## 📁 Step 1 — Copy libraries

Create this folder if it does not already exist:

```
app/libs
```

Then place the following files inside it:

```
api-82.jar
api-82-sources.jar
```

Your structure should look like:

```
app/
 ├─ libs/
 │   ├─ api-82.jar
 │   └─ api-82-sources.jar
```

---

## 🔧 Step 2 — Add Gradle dependency entries

Open:

```
app/build.gradle
```

Add these lines inside the `dependencies { ... }` block:

```
dependencies {
    compileOnly(files("libs/api-82.jar"))
    compileOnly(files("libs/api-82-sources.jar"))
}
```

This ensures the Xposed API is:

* available at compile time
* **not packaged into your APK**
* resolved correctly by Android Studio

---

## 📝 Notes

* `compileOnly` is required because LSPosed/Xposed provides the API at runtime
* these JARs must match your LSPosed/Xposed API version (here: **82**)
* if sync fails, ensure:

  * filename matches exactly
  * folder name is exactly `libs`
  * Gradle sync is rerun

---

##  After setup

1. Sync Gradle
2. Rebuild the project
3. Android Studio should now resolve imports like:

```
de.robv.android.xposed.*
```

---

