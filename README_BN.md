# MAYA – Android Virtual Girlfriend (Starter)

এটি একটি Android Studio starter project। এতে আছে:
- বাংলা চ্যাট UI
- বাংলা voice input (Android Speech Recognizer)
- বাংলা text-to-speech reply
- সর্বশেষ ৩০টি মেসেজ লোকালি সংরক্ষণ
- প্রতিদিন সকাল ৮টা, দুপুর ১টা, রাত ৯টার local notification
- AI response-এর জন্য আলাদা Node.js backend proxy

## গুরুত্বপূর্ণ সীমাবদ্ধতা
এটি এখনো install-ready APK নয়; Android Studio-তে build করতে হবে।
AI চালাতে backend server চালু করে একটি বৈধ API key দিতে হবে। API key কখনো APK-তে রাখবেন না।
Voice recognition এবং TTS-এর মান Android ডিভাইসের speech service ও installed voice-এর ওপর নির্ভর করে।
Android 13+ এ notification permission দিতে হবে। Battery optimization/OEM restrictions-এর কারণে
কিছু ফোনে notification দেরি হতে পারে।

## Android app চালানো
1. Android Studio-তে এই project folder Open করুন।
2. Gradle sync শেষ হতে দিন।
3. ফোনে Developer options ও USB debugging চালু করে Run দিন।
4. ফোনে `10.0.2.2` কাজ করবে না—এটি Android Emulator-এর localhost alias।
   বাস্তব ফোনে `MAYA`-র server URL-এ আপনার server-এর HTTPS address বসাতে হবে।
5. Microphone ও notification permission দিন।

## Backend চালানো
Node.js 18+ দরকার।

```bash
cd backend
npm install
# Linux/macOS:
export OPENAI_API_KEY="your_api_key"
export OPENAI_MODEL="gpt-4o-mini"
npm start
```

বাস্তব ফোনে নিরাপদ HTTPS hosting ব্যবহার করুন। Android app-এর default server URL emulator-এর জন্য
`http://10.0.2.2:3000`। বাস্তব ফোনে অ্যাপের উপরের `AI সার্ভারের URL` ঘরে আপনার HTTPS server address লিখে `সেভ` চাপুন।

## পরবর্তী উন্নয়ন
- Settings screen: server URL, AI model, voice on/off
- ব্যক্তিত্ব ও memory profile সম্পাদনা
- Android 13 notification permission onboarding
- Secure account/authentication, HTTPS, rate limiting
- APK signing ও release build
