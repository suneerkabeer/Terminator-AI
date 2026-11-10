# Suneer AI — starter prototype

A responsive, installable web app starter for Android and PC. It stores chats and personal memory in the browser on the current device, supports export backup, and has connection settings for Ollama and OpenAI-compatible APIs.

## Important limitations
- This is a **starter prototype**, not a finished native Android APK.
- Chat history and personal memory are local to each browser/device. Cross-device encrypted sync is not implemented yet.
- Local Ollama requires an Ollama server running on a PC or another host. Android can connect to it over a trusted Wi-Fi LAN if the server is configured for LAN access and CORS/network permissions are handled.
- Online providers may impose free-tier quotas, change models, or require billing. No app can guarantee unlimited high-end online AI for free.
- API keys are stored in browser local storage in this prototype. Do not use a valuable key on a shared device. A production version should use encrypted secure storage or a private backend.
- The offline app shell works without internet after first load, but AI replies require a reachable local or online model.

## Run on PC
Serve this folder over localhost (service workers need localhost or HTTPS):
```bash
python -m http.server 8080
```
Open `http://localhost:8080`.

## Install on Android
1. Put the app on an HTTPS host you control, or serve it on your trusted local network for testing.
2. Open it in Chrome on Android.
3. Use Chrome menu → Add to Home screen / Install app.
4. For a production native Android package, wrap this PWA with Capacitor or build a dedicated Kotlin app.

## Connect Ollama on PC
1. Install Ollama on the PC from its official website.
2. Pull a small model suitable for your PC, for example `qwen2.5:3b` (model choice depends on RAM).
3. Start Ollama and confirm the API is reachable at `http://127.0.0.1:11434`.
4. On the phone, set the Ollama URL to the PC's LAN address, e.g. `http://192.168.1.20:11434`, after configuring Ollama to listen on the LAN and allowing the port through the firewall.
5. Both devices must be on the same trusted Wi-Fi network. Avoid exposing Ollama directly to the public internet.

## Next engineering milestones
1. Replace browser localStorage with IndexedDB and encrypted per-user database.
2. Implement cross-device sync with end-to-end encryption and device pairing.
3. Add Android local inference using llama.cpp with a quantized model sized for the phone.
4. Add streaming responses, cancellation, attachments, image model support and voice input/output.
5. Add provider adapters with clear rate-limit and privacy disclosures.
6. Package as Android APK/AAB using Capacitor or native Kotlin.
