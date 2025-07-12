
# AI Email Reply Generator Chrome Extension 

![Java](https://img.shields.io/badge/Java-17-blue?logo=java)  
![Spring Boot](https://img.shields.io/badge/SpringBoot-3.2-green?logo=spring)  
![Chrome Extension](https://img.shields.io/badge/Chrome%20Extension-enabled-brightgreen?logo=googlechrome)  
![API](https://img.shields.io/badge/Backend-REST%20API-orange)  
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

### Description

**AI Email Reply Generator** is a powerful productivity tool that combines a Spring Boot backend with a Chrome extension to help you write **AI-generated email replies** directly inside **Gmail**.

Powered by Google Gemini API  
Supports custom tone like `friendly`, `professional`, `casual`  
No need to copy/paste – reply is inserted directly into Gmail's compose box

---

### Tech Stack

| Layer          | Technology            |
|----------------|------------------------|
| Frontend       | Chrome Extension (JavaScript) |
| Backend        | Spring Boot (Java 17)         |
| AI Integration | Google Gemini (Generative Language API) |
| Communication  | REST API via WebClient        |

---

### How It Works

1. The Chrome extension detects when you open the Gmail compose window.
2. It injects an `AI Reply` button into Gmail's toolbar.
3. When clicked, it:
   - Captures the original email content
   - Sends it to the Spring Boot backend
4. Spring Boot:
   - Builds a natural language prompt
   - Sends the request to Gemini API
   - Parses and returns the AI-generated reply
5. The Chrome extension inserts the reply directly into Gmail's compose box.

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

- Set the following in your `application.properties`:

```properties
GEMINI_URL=https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent
GEMINI_KEY=your_api_key_here
```

> You can also set them as environment variables: `GEMINI_URL`, `GEMINI_KEY`

- Then run the Spring Boot app:

```bash
./mvnw spring-boot:run
```

Or in IntelliJ: Run the `EmailWriterApplication.java` class

---

#### ✅ 3. Load the Chrome Extension

- Open Chrome → `chrome://extensions/`
- Enable **Developer mode**
- Click **Load unpacked**
- Select the `chrome-extension` folder

---

### Test Flow

1. Go to Gmail → Click **Compose**
2. You’ll see an **“AI Reply”** button
3. Click it → The extension fetches the reply from the backend
4. The AI-generated reply appears in your Gmail compose box

---

### Screenshots

> Add your screenshots here:
- ✉ Gmail Compose with AI Reply button
![screenshot](https://raw.githubusercontent.com/premc5731/AI-Email-Reply-Chrome-Extension/main/Screenshots/Reply_button.png
)

---

### To-Do / Future Improvements

- Add support for multiple tones via dropdown
- UI enhancements using Material UI in popup
- OAuth integration for Gmail auth
- Store logs or reply history

---

### Disclaimer

This tool uses **Google Gemini API**. You must have your own API key and comply with their terms of use.

---

### License

This project is licensed under the [MIT License](LICENSE).
