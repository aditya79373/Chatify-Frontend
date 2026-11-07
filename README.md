# Chatify Frontend

A real-time chat app that runs in the browser, as a native **Windows** desktop app and as an **Android** app, built with Tauri.

The server lives in a separate repository: **Chatify-Backend**.

## Features

- **Real-time messaging** over WebSockets (Socket.IO).
- **Sign in** with email, with account emails sent by the backend.
- **Media sharing**, with an emoji picker in the message box.
- **Live website**: use Chatify directly in the browser at https://chatifyapp-s11a.onrender.com/, no setup needed.
- **Download page**: the website has a section where you can download the Windows and Android apps.
- **Desktop app** (Tauri, Windows): launch at startup, deep links and automatic updates.
- **Android app**: the same app on your phone.
- **Light and dark themes** and a responsive layout.

## Tech stack

| Area | Tools |
| --- | --- |
| UI | React 18, TypeScript, Vite, Tailwind CSS, Radix UI, lucide-react, sonner |
| Routing and data | React Router, TanStack Query, React Hook Form, Zod |
| Realtime and backend services | socket.io-client, Supabase JS client |
| Desktop and Android | Tauri 2 (autostart, deep-link, updater, store, fs plugins) |
| Android tooling | Android Studio (Android SDK, NDK, emulator) |
| Package manager | npm |

## Getting started

### Use the live website

You can use Chatify directly without running anything locally:

**https://chatifyapp-s11a.onrender.com/**

From there you can chat in the browser, or download the **Windows** or **Android** app from the download section.

### Prerequisites

- Node.js (LTS)
- npm (comes with Node.js)
- The Chatify backend running (see the **Chatify-Backend** repository)
- For the desktop and Android apps only: the [Rust toolchain and Tauri prerequisites](https://tauri.app/start/prerequisites/) for your OS
- For the Android app only: Android Studio with the Android SDK and NDK, and the `JAVA_HOME` and `ANDROID_HOME` environment variables set

### Clone

```bash
git clone https://github.com/aditya79373/Chatify-Frontend.git
cd Chatify-Frontend
```

### Install and run

```bash
npm install
npm run dev
```

Open the URL Vite prints (usually http://localhost:5173).

### Download the apps

Once the website opens, use its download section to get the **Windows** or **Android** app, then install and use it from there. You don't need to build the apps yourself unless you want to develop them (see below).

### Desktop app (Tauri)

```bash
npm run tauri:dev     # run the desktop app in development
npm run tauri:build   # build an installer for your OS
```

### Android app (Tauri)

```bash
npm run tauri android init    # first time only: creates the Android project
npm run tauri android dev     # run on a connected phone or an emulator
npm run tauri android build   # build the APK / AAB
```

Connect your phone with USB debugging turned on, or start an emulator from Android Studio, before running `android dev`.

You can also open the generated Android project in **Android Studio** (`src-tauri/gen/android`) to run it, debug it, or build a signed APK / AAB.

The web layout is responsive, so the same screens work on phone-sized displays.

### Build for the web

```bash
npm run build
npm run preview       # optional: preview the production build
```

## Scripts

| Script | What it does |
| --- | --- |
| `dev` | Start the Vite dev server |
| `build` | Production build |
| `preview` | Preview the production build |
| `tauri:dev` | Run the desktop app in development |
| `tauri:build` | Build the desktop app installer |
| `tauri android dev` | Run the Android app (use `npm run tauri android dev`) |

## Notes

- Do not commit `.env` files.
- The web, desktop and Android apps share the same code. Only the Tauri commands above are specific to the desktop and Android builds.
