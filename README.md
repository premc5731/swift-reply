
# AI Email Reply Generator Chrome Extension 

![Java](https://img.shields.io/badge/Java-17-blue?logo=java)  
![Spring Boot](https://img.shields.io/badge/SpringBoot-3.2-green?logo=spring)  
![Chrome Extension](https://img.shields.io/badge/Chrome%20Extension-enabled-brightgreen?logo=googlechrome)  
![API](https://img.shields.io/badge/Backend-REST%20API-orange)  

---

### Description

**AI Email Reply Generator** is a productivity tool that combines a Spring Boot backend and a Chrome extension to help you write **AI-generated email replies** directly inside **Gmail**.

- Powered by Google Gemini API  
- Supports tones like `friendly`, `professional`, `casual`  
- No need to copy/paste – reply is inserted into Gmail's compose box

---

### Tech Stack

| Layer          | Technology                        |
|----------------|------------------------------------|
| Frontend       | Chrome Extension (JavaScript)      |
| Backend        | Spring Boot (Java 17)              |
| AI Integration | Google Gemini (Generative API)     |
| Communication  | REST API via WebClient             |

---

### How It Works

1. Chrome extension detects Gmail compose window.
2. Injects `AI Reply` button into Gmail's toolbar.
3. On click:
   - Captures original email content
   - Sends to Spring Boot backend
4. Spring Boot:
   - Builds prompt
   - Sends request to Gemini API
   - Returns generated reply
5. Reply is inserted into Gmail compose box.

---

### Project Structure

```
📁 email-writer
 ├── 📦 backend
 │   ├── EmailGeneratorService.java
 │   ├── EmailGeneratorController.java
 │   ├── EmailRequest.java
 │   └── application.properties
 └── 📦 chrome-extension
     ├── content.js
     ├── manifest.json
     └── icons/
```

---

### Getting Started

#### ✅ 1. Clone the Repository

```bash
git clone https://github.com/your-username/ai-email-writer.git
cd ai-email-writer
```

#### ✅ 2. Set Up the Backend (Spring Boot)

In `application.properties`:

```properties
GEMINI_URL=https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent
GEMINI_KEY=your_api_key_here
```

Or set environment variables: `GEMINI_URL`, `GEMINI_KEY`

Then run:

```bash
./mvnw spring-boot:run
```
Or run `EmailWriterApplication.java` in IntelliJ.

---

#### ✅ 3. Load the Chrome Extension

- Open Chrome → `chrome://extensions/`
- Enable **Developer mode**
- Click **Load unpacked**
- Select `chrome-extension` folder

---

### Test Flow

1. Go to Gmail → Click **Compose**
2. Click **“AI Reply”** button
3. Extension fetches reply from backend
4. Reply appears in Gmail compose box

---

### Downloads (JAR & Extension)

Check the `downloads/` folder:

| File                          | Purpose                            |
|-------------------------------|------------------------------------|
| `email-writer-backend.jar`    | Executable Spring Boot backend JAR |
| `email-extension.zip`         | Chrome extension (zipped folder)   |

####  How to Use

1. **Run Backend**:
```bash
java -jar downloads/email-writer-backend.jar
```

2. **Load Extension**:
- Unzip `email-extension.zip`
- Go to Chrome → `chrome://extensions/`
- Click **Load unpacked** and select unzipped folder

---

### Screenshots

> ✉ Gmail Compose with AI Reply button  
![screenshot](https://raw.githubusercontent.com/premc5731/AI-Email-Reply-Chrome-Extension/main/Screenshots/Reply_button.png)

---

### To-Do / Future Enhancements

- Tone selector dropdown (UI)
- Add Material UI popup
- Gmail OAuth login
- Reply history/logs

---

### Disclaimer

Uses Google Gemini API. Requires your own API key. Follow Google's API terms.

---

### License

This project is licensed under the [MIT License](LICENSE).
