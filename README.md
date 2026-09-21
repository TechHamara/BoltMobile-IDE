# 🚀 BoltMobile IDE: The Ultimate On-Device Extension Builder for App Inventor, Kodular & Niotron!

Hello Developers! 👋

We are thrilled to introduce **BoltMobile IDE** – a revolutionary Android application that brings the full power of desktop extension building directly to your smartphone and tablet. 

Whether you build for **MIT App Inventor**, **Kodular**, or **Niotron**, BoltMobile IDE allows you to create, code, optimize, and compile production-ready `.aix` extensions **100% offline and natively on your Android device**—no PC, no cloud server, and no Termux setup required!

---

## 🌟 Comprehensive Feature Overview

BoltMobile IDE brings the full feature set of the legendary **Bolt CLI** to mobile, packed with modern developer tools tailored for on-the-go coding:

### 🛠️ 1. High-Performance On-Device Compilation
- **⚡ Lightning-Fast Builds:** Optimized compilation pipelines compile, dex, and package extensions in just seconds. Success and error dialogs display precise **millisecond-level build metrics** (e.g., `1s 230ms` or `780ms`).
- **☕ Kotlin & Java Language Support:** Write your extensions in pure Java, Kotlin, or both simultaneously in the same project! The compiler smartly bypasses Kotlin steps when only Java files are detected for maximum build speed.
- **📡 On-Device AIDL Compilation:** Need Android Interface Definition Language (AIDL) for IPC communication? Drop your `.aidl` files into `src/`. The IDE automatically invokes bundled native AIDL tooling to generate `.java` interface stubs and seamlessly integrates them into the ECJ classpath before building!
- **🎨 Red Drop-down Blocks:** Full support for App Inventor's `@Options` annotation to generate beautiful, type-safe helper blocks and enum parameters.
- **📄 Automatic Documentation:** Generates a clean, formatted Markdown catalog (`extension.txt`) in your `out/` folder on every build, listing your component description, author details, and compiled `.aix` file size.

### 💻 2. Professional Sora Code Editor
- **🎨 Desktop-Grade Highlighting:** Powered by the robust **Sora Editor** engine with TextMate grammar support, VS Code-style color themes, and smooth scrolling.
- **⌨️ Virtual Coding Keyboard Row:** A dedicated, scrollable quick-access symbol bar floats above your soft keyboard:
  `Tab`, `{`, `}`, `(`, `)`, `[`, `]`, `<`, `>`, `;`, `:`, `"`, `'`, `=`, `+`, `-`, `*`, `/`, `_`, `$`, `@`, `&`, `|`, `!`, `?`, `#`, `%`, `^`, `\`
  The top toolbar automatically hides when typing to maximize screen real estate!
- **🔍 Productivity Essentials:** Integrated Undo, Redo, fast text search, and 1-tap file sharing.
- **⚙️ Editor Customization:** Instant toggles for auto-bracket completion `{ }`, `( )`, pinch-to-zoom scaling, line numbering, and live suggestions.

### 🧠 3. Intelligent Code Autocompletion (`Ai2LangWrapper`)
- **💡 Contextual Suggestions:** Real-time autocompletion for standard Java and Android SDK APIs (`String`, `Context`, `View`, `Intent`, etc.).
- **🧩 Pre-Indexed App Inventor Ecosystem:** Comes pre-loaded with essential extension classes and annotations:
  `@DesignerComponent`, `@SimpleFunction`, `@SimpleProperty`, `@SimpleEvent`, `@UsesPermissions`, `AndroidNonvisibleComponent`, `ComponentContainer`, and more.
- **📦 Smart Import Completion:** Typing `import com.google.appinventor...` auto-completes full package paths effortlessly.
- **🔄 Dynamic In-File Scanning:** The editor continuously analyzes your open file to suggest custom variables, local methods, and parameter names as you type.

### 📦 4. Visual Dependency Manager & Maven Resolution
- **🔎 Graphical Maven Search:** Tap the **Extension / Puzzle icon** in the top bar to search the entire **Maven Central** repository directly from the app!
- **⚡ One-Tap Dependency Injection:** Find the library you need (e.g., `gson`, `okhttp`, `glide`), select your version, and hit **Add**. The IDE automatically formats and updates your `bolt.yml` configuration.
- **🌐 Dynamic Maven Resolver:** When you sync, the IDE downloads `.aar` or `.jar` binaries, parses POM metadata, resolves transitive requirements, and extracts classes directly into your `deps/` directory.
- **📁 Smart `deps/` Merging:** Local JAR/AAR packages dropped into `deps/` are scanned, duplicate `META-INF` conflicts are removed, and classes are safely merged into the `.aix` archive.

### 🛡️ 5. Advanced Security, Shading & Bytecode Protection
- **🔒 StrGuard Bytecode String Obfuscation:** Built-in bytecode encryption protects hardcoded strings, API keys, secrets, and URLs against reverse engineering and decompilation. Easily configured via `bolt.yml` (`enabled`, `key`, `packages`). The runtime decryption stub is automatically embedded into your compiled `.aix`.
- **🔄 Package Relocation (JarJar Shading):** Fat libraries causing duplicate class collisions? Enable `EnableAutoRelocation: true` in `bolt.yml` to rename class packages at the bytecode level.
- **⚡ ProGuard & R8 Optimization:** Strip unused code and minify binaries. Need reflection? Configure `minimize:` exclusions (`exclude_dependency`, `exclude_project`) in `bolt.yml` to prevent R8 from shrinking reflection-heavy classes.
- **☕ Core Library Desugaring:** Safely use modern Java 8+ features (such as `java.util.stream` and `java.time`) while preserving backward compatibility on older Android devices.

### 🧩 6. Native C/C++ (.so) & Custom XML Support
- **⚙️ Custom AndroidManifest & Layouts:** Inject custom layouts, values, and manifests using `@UsesXmls` and `src/AndroidManifest.xml` with automatic shorthand class expansion.
- **🧩 JNI Native Libraries (.so):** Full support for `jni/` structures (`armeabi-v7a`, `arm64-v8a`, `x86`, `x86_64`) via `@UsesNativeLibraries`. The IDE maps ABI suffixes and packages binaries into the `.aix` according to official MIT App Inventor build server standards.

### 📂 7. Scoped Storage (SAF) & External Editor Compatibility
- **🔒 Android 11+ Scoped Storage:** Uses Android's modern Storage Access Framework (SAF). Pick your workspace folder once and your projects stay safe even if the app is reinstalled.
- **🤝 External Editor Workflow:** Love coding in **Acode** or **Termux**? BoltMobile IDE detects external changes, clears internal memory caches before compiling, and builds your absolute latest code without overwriting edits!
- **🔄 Git Integration:** Clone repositories, manage branches, and pull updates natively from your phone.
- **🩹 Project Auto-Repair:** Accidentally deleted `bolt.yml` or `AndroidManifest.xml`? Hitting Sync or Build automatically scaffolds missing project structures.

---

## ❓ Frequently Asked Questions (FAQ)

**Q: Do I need an active internet connection to compile?**  
**A:** No! The entire compilation pipeline (Java, Kotlin, AIDL, ECJ, D8, DX, R8) runs 100% offline on your device processor. Internet is only required when you choose to download remote Maven libraries or perform Git operations.

**Q: Does it work on modern Android 13, 14, and 15?**  
**A:** Yes! BoltMobile IDE strictly uses Android's Storage Access Framework (SAF) with zero broad-storage permission requirements, ensuring full compatibility with modern Android versions and Google Play policies.

**Q: Can I use third-party `.jar` and `.aar` libraries?**  
**A:** Yes! You can search and add them via the **Visual Dependency Manager**, declare coordinates in `bolt.yml`, or manually place `.jar`/`.aar` files into the `deps/` folder. The compiler handles extracting, shading, and dexing automatically.

**Q: Can I edit files in external editors like Acode?**  
**A:** Absolutely. You can edit your project files using Acode, QuickEdit, or Termux. When you return to BoltMobile IDE and hit **Build**, it reloads files directly from storage before compiling.

**Q: Where can I find the compiled extension?**  
**A:** Your compiled `.aix` file is saved inside the `out/` folder of your project, along with `extension.txt` containing your auto-generated documentation. You can share it directly via the Android Share sheet.

**Q: Does BoltMobile IDE support multi-component extensions and Red Blocks?**  
**A:** Yes! Multiple `@DesignerComponent` declarations in a single project and App Inventor `@Options` annotations (Red Blocks) are fully supported.

---

## 📥 Getting Started in 3 Simple Steps

1. **Map Your Workspace:** Open BoltMobile IDE and select a folder on your device storage (e.g., `Documents/BoltProjects`).
2. **Create a Project:** Tap **New Project**, enter your extension name and package identifier (e.g., `io.th.boltide.myextension`).
3. **Code & Build:** Write your code with live autocompletion, add dependencies with the Visual Manager, and hit **Build** to generate your `.aix`!

---

### 💬 Feedback & Community Support
BoltMobile IDE is built with passion by **TechHamara** to empower the extension developer community. 

- **GitHub Repository:** https://github.com/TechHamara/BoltMobile-IDE
- **Bug Reports & Feature Requests:** https://github.com/TechHamara/BoltMobile-IDE/issues
- **Contact:** support@techhamara.com

*Disclaimer: BoltMobile IDE is an independent open development tool developed by TechHamara. It is not affiliated with, endorsed by, or sponsored by MIT, Kodular, Niotron, or Google LLC.*

Happy Extension Building! 💻🔥
