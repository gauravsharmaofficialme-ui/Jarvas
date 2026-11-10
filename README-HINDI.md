# J.A.R.V.I.S. AI – Android + Website (V1)

यह पहला Free Demo संस्करण है। इसमें responsive वेबसाइट/PWA, Demo Chat, हिंदी/English voice input (browser support पर निर्भर), text-to-speech, basic local memory toggle और Google Web Search shortcut है।

## जरूरी बातें
- Free Demo बिना AI API key के चलता है।
- असली AI जोड़ने पर API key केवल server/Render Environment में रखें। उसे `public/app.js` या HTML में कभी न डालें।
- पुरुष आवाज़ की उपलब्धता Android/Chrome में इंस्टॉल voice packs पर निर्भर है। कोड पुरुष जैसी आवाज़ को प्राथमिकता देता है, लेकिन हर डिवाइस पर इसकी गारंटी नहीं।
- Voice recognition के लिए इंटरनेट और microphone permission की जरूरत हो सकती है।
- Android/Computer control अभी सुरक्षित demo में शामिल नहीं है। आगे इसे केवल स्पष्ट अनुमति वाले सीमित कार्यों के साथ जोड़ा जाएगा।
- Memory डिफ़ॉल्ट रूप से बंद है। चालू करने पर चैट का सीमित इतिहास उसी ब्राउज़र के localStorage में सेव होगा। इसे बंद करने पर सेव इतिहास हट जाएगा।
- Web Search बटन Google Search खोलता है; यह अभी AI द्वारा स्वतः वेब पढ़ने वाला search engine integration नहीं है।

## स्थानीय रूप से चलाना
Node.js 18 या नया संस्करण चाहिए।

```bash
npm install
npm start
```

फिर ब्राउज़र में `http://localhost:3000` खोलें।

## GitHub पर अपलोड (Android Chrome)
1. GitHub में नया repository बनाएं: `jarvis-ai`।
2. ZIP को extract करें।
3. सभी फाइलें और `public` folder repository के root में upload करें।
4. `.env` फाइल upload न करें। `.env.example` सुरक्षित template है।

## Render पर deploy
1. Render Dashboard → New + → Web Service।
2. GitHub repository `jarvis-ai` connect करें।
3. Runtime: Node चुनें।
4. Build Command: `npm install`
5. Start Command: `npm start`
6. Deploy Web Service दबाएँ।
7. Deploy पूरा होने पर Render URL खोलें।

## Android पर ऐप की तरह install
1. Render URL को Android Chrome में खोलें।
2. Chrome के तीन डॉट → `Add to Home screen` या `Install app` चुनें।
3. नाम `J.A.R.V.I.S.` रखें और Add दबाएँ।

## असली AI बाद में जोड़ना
Render → आपकी Web Service → Environment में ये variables जोड़ें:
- `AI_API_KEY` = आपके AI provider की secret key
- `AI_BASE_URL` = provider का compatible API base URL
- `AI_MODEL` = आपके provider का उपलब्ध model

फिर Save/Deploy करें। API key कभी भी public GitHub repository में न डालें।

## आम समस्याएँ
- `Application failed to respond`: Render Logs देखें; Node version 18+ और `npm start` जाँचें।
- माइक काम नहीं करता: Chrome में खोलें, site microphone permission Allow करें और HTTPS URL इस्तेमाल करें।
- हिंदी/पुरुष आवाज़ नहीं आती: Android Settings → Text-to-speech output में Hindi voice data install करें; voice selection डिवाइस के अनुसार बदल सकती है।
