**English** | [中文](README.md)

## I. About

Layout Inspect is an essential reverse engineering tool. It lets you view the current activity, capture layouts on the fly, inspect running processes, force-launch Activities, enumerate ClassLoaders, search for dynamically loaded classes, inject .so files, dump Dex with custom options, decrypt Assets and XML resources, bypass screenshot restrictions, debug webviews, and more.

<img src="https://i.imgs.ovh/2025/12/10/CnLUhd.jpeg" alt="">

## II. Getting Started

1. Install Layout Inspect, then enable it in LSPosed for whichever apps you want to hook.

2. The module also supports API 100 and lets you request scopes dynamically from within the app.

[Heads up:](#) You don't need to enable the "System" scope (but it won't break anything if you do).

## III. Features

### 1. Current Activity

View the currently running Activity along with its Application and Intent.

### 2. Layout Capture (Flagship Feature)

Quickly locate any View. Works on any window type—PopupWindow, Dialog, Menu, floating windows, you name it.

View Info:

- View (General):
-
    - Class name (class)
-
    - Width (width)
-
    - Height (height)
-
    - id
-
    - tag
-
    - contentDescription
-
    - Foreground (foreground)
-
    - Background (background)
-
    - Listener info (listenInfo): pinpoint click handlers, long-press listeners, etc.
-
    - Padding (padding)
-
    - Margin (margin)
- TextView:
-
    - Text content (text)
-
    - Text size (textSize)
-
    - Text color (textColor)
-
    - Hint color (hintColor)
- AdapterView (most lists):
-
    - Adapter (adapter)
- VideoView:
-
    - URI (uri)
-
    - Headers (headers)
- WebView:
-
    - URL (url)
-
    - cookie
-
    - UserAgent
-
    - javascriptInterfaces (the Java↔WebView bridge)
- ImageView:
-
    - Image source (src)—replaceable

---

View Actions:

- Export any View as an image
- [Call Stack:](#) Trace how a View was created so you can jump straight to the relevant code

---

[God Mode (Temporary):](#)

- View (General)—modify:
-
    - Width (width)
-
    - Height (height)
-
    - Foreground (foreground)
-
    - Background (background)
-
    - Padding (padding)
-
    - Margin (margin)
-
    - Remove View
-
    - Hide View ⇆ Show View
- TextView—modify:
-
    - Text content (text)
-
    - Text size (textSize)
-
    - Text color (textColor)
-
    - Hint color (hintColor)
- WebView—modify:
-
    - URL (url)
-
    - Inject Javascript
-
    - UserAgent
- ImageView—modify:
-
    - Image source (src)

---

### 3. App Processes

Two panels—"Current Process" and "More Processes"—showing all running processes for the target app.

### 4. Activity Manager

Lists every Activity declared by the target app. Tap any of them to launch it directly.

### 5. ClassLoader

Enumerates all ClassLoaders in the app. From here you can preview objects or dump them.

### 6. Class Search

More thorough than Reflection Master: searches by enumerating ClassLoaders, so it catches externally loaded Dex files too.

### 7. .so Injection

Inject native libraries (.so files) into the target app to unlock additional capabilities.

### 8. Dex Dump

More comprehensive than most modules:

- Dump from any ClassLoader
- Dump a specific mCookie from a given ClassLoader
- Force-load classes via R8 rules or regex, then dump (fixes nop issues)

### 9. XML Dump (Exclusive)

Decrypts common AXML obfuscation (e.g., Epic) by parsing the raw xmlBlock memory. Niche, but a lifesaver when you need it.

### 10. Asset Dump

Decrypts common Asset-level encryption used by NP Manager, Epic, Muhua, Zhipian, and others.

### 11. Screenshot Restriction Bypass

Unlike other modules that hook and intercept, this one disables restrictions via direct invocation. If you don't use it, the target app stays untouched.

### 12. WebView Debugging

For reversing web-heavy apps. Pairs with Chrome DevTools for live inspection of HTML elements, network requests, and algorithm tracing—saves hours.

## IV. FAQ

### Floating window getting buried?

The floating window priority has been tuned, but nothing's 100%. If it gets covered, [double-tap volume up or down within one second](#) to bring it back.
