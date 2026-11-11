# NCERT AI Teacher — Android APK wrapper

यह Android Studio प्रोजेक्ट आपके Streamlit NCERT AI Teacher को Android ऐप के रूप में खोलता है।
**यह अभी तैयार APK नहीं है।** APK बनाने से पहले Python/Streamlit ऐप को इंटरनेट पर deploy करना और नीचे URL सेट करना जरूरी है।

## जरूरी बात
- Android ऐप एक WebView wrapper है; असली AI और PDF processing आपके ऑनलाइन Streamlit server पर चलेगी।
- मोबाइल में इंटरनेट चाहिए।
- OpenAI API key केवल Streamlit server के सुरक्षित Secrets/Environment में रखें। APK में API key न डालें।
- PDF अपलोड के लिए Android file picker सपोर्ट जोड़ा गया है।

## चरण 1: Python ऐप deploy करें
1. `ncert_ai_teacher_complete.zip` को extract करें।
2. `app.py` और `requirements.txt` को किसी भरोसेमंद Streamlit hosting service पर deploy करें।
3. Hosting dashboard के Secrets/Environment में `OPENAI_API_KEY` सेट करें।
4. Deploy होने के बाद मिलने वाला HTTPS URL कॉपी करें।

## चरण 2: Android URL सेट करें
इस फाइल को खोलें:
`app/src/main/res/values/strings.xml`

इस लाइन में:
`https://YOUR-STREAMLIT-APP-URL.streamlit.app`

अपना असली HTTPS deployment URL डालें।

## चरण 3: APK बनाएँ
1. Android Studio में यह `ncert_teacher_android` folder खोलें।
2. Android SDK Platform 35 और JDK 17 उपलब्ध होने दें।
3. Gradle sync पूरा होने दें।
4. Menu: **Build > Build Bundle(s) / APK(s) > Build APK(s)** चुनें।
5. APK आमतौर पर `app/build/outputs/apk/debug/app-debug.apk` में मिलेगा।
6. APK को अपने Android फोन में भेजकर install करें। फोन पूछे तो केवल अपने बनाए/भरोसेमंद APK के लिए install permission दें।

## अभी बाकी काम
- असली hosted Streamlit URL डालना।
- Android Studio से build करके फोन पर जाँचना।
- Production release के लिए signed APK बनाना।

## सुरक्षा
API key को Android source code, APK, Git repository या सार्वजनिक संदेश में कभी न रखें।
