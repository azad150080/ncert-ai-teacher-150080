# NCERT AI Teacher — मोबाइल से APK बनाने की फाइलें

इस repository में दो हिस्से हैं:
- `app.py` और `requirements.txt`: ऑनलाइन Streamlit ऐप (AI/PDF यहीं चलेंगे)
- `android-app/`: Android ऐप का WebView wrapper
- `.github/workflows/build-apk.yml`: GitHub Actions से APK बनाने की प्रक्रिया

**यह ZIP अपने-आप APK नहीं है।** पहले Streamlit ऐप को ऑनलाइन चलाना होगा, फिर GitHub Actions APK बनाएगा।

## मोबाइल से करने के चरण

### 1. इस ZIP को GitHub पर डालें
1. GitHub में sign in करें और `New repository` दबाएँ।
2. Repository का नाम `ncert-ai-teacher` रखें और **Private** चुनें।
3. Repository बनने पर `Add file` → `Upload files` चुनें।
4. ZIP को फोन में extract करें, फिर उसके अंदर की सभी फाइलें और `.github` folder repository में upload करें। ध्यान दें: `app.py` repository के मुख्य पेज/root में होना चाहिए।
5. `Commit changes` दबाएँ।

### 2. Streamlit ऐप ऑनलाइन deploy करें
1. https://share.streamlit.io/ खोलें और GitHub से sign in करें।
2. `Create app` चुनें; अपनी repository, branch `main`, और main file path `app.py` चुनें।
3. Advanced settings / Secrets में यह जोड़ें:

```toml
OPENAI_API_KEY = "अपनी-API-key"
```

4. Deploy करें और ऐप का HTTPS URL कॉपी करें। API key केवल Streamlit Secrets में रखें—GitHub code, APK या किसी chat में नहीं।

### 3. GitHub में Streamlit URL variable जोड़ें
1. अपनी GitHub repository खोलें → `Settings` → `Secrets and variables` → `Actions` → `Variables`।
2. `New repository variable` दबाएँ।
3. Name: `STREAMLIT_APP_URL`
4. Value: Streamlit से मिला पूरा HTTPS URL, जैसे `https://your-app-name.streamlit.app`
5. Save करें।

### 4. APK बनवाएँ और डाउनलोड करें
1. Repository में `Actions` tab खोलें।
2. `Build NCERT AI Teacher APK` workflow चुनें।
3. `Run workflow` दबाएँ। Build पूरा होने तक प्रतीक्षा करें।
4. सफल run खोलें; नीचे `Artifacts` में `ncert-ai-teacher-debug-apk` डाउनलोड करें।
5. ZIP खोलकर `app-debug.apk` निकालें और अपने Android फोन में install करें। केवल अपने भरोसेमंद build को install करें।

## जरूरी सुरक्षा और सीमाएँ
- Android wrapper को चलाने के लिए इंटरनेट चाहिए।
- AI और PDF processing ऑनलाइन Streamlit server पर होगी।
- OpenAI API key कभी भी APK या GitHub repository में न डालें।
- यह workflow debug APK बनाता है, Play Store के लिए signed release नहीं।
- GitHub Actions build fail हो तो Actions run का error message देखकर उसे ठीक करना होगा।
