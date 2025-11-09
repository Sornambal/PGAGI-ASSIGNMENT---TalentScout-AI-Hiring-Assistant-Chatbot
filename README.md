# 🧠 TalentScout — AI Hiring Assistant Chatbot

### 👩‍💻 Internship Project — AI/ML Intern Assignment  
**Developer:** Sornambal Palanisamy  
**Platform:** Google Colab (Gradio-based UI)  
**Tech Stack:** Python • Gradio • OpenAI API (GPT-4/3.5) • SQLite • Cryptography  

---

## 🚀 Project Overview

**TalentScout Hiring Assistant** is an AI-powered chatbot designed to automate the **initial screening process** for candidates applying to technology roles.  

It interacts conversationally to:
- Collect essential candidate information  
- Understand their tech stack  
- Generate tailored **technical interview questions**  
- Store responses securely for recruiter review  

This project demonstrates the use of **LLMs (Large Language Models)** for intelligent dialogue handling and **prompt engineering** for dynamic content generation.

---

## 🎯 Key Functionalities

| Feature | Description |
|----------|--------------|
| 🤝 Greeting & Introduction | Bot welcomes the user and explains its purpose |
| 🧍 Candidate Information Collection | Gathers name, email, phone, experience, position, and location |
| 🧠 Tech Stack Detection | Accepts technologies like Python, Django, React, etc. |
| ⚙️ Dynamic Question Generation | Uses LLMs to create 3–5 relevant technical questions per tech |
| 🗂️ Context Handling | Maintains chat flow and avoids repetition |
| 🧩 Fallback Responses | Provides meaningful prompts for invalid inputs |
| 🔐 Secure Data Handling | Stores encrypted candidate details in SQLite |
| ✅ Graceful Conversation End | Thanks the user and outlines next steps upon exit |
| 💾 Simulated Data Storage | Stores responses locally in `talentscout.db` |
| 📦 Optional | Can be deployed on Streamlit Cloud / Hugging Face Spaces |

---

## 🧰 Tech Stack

| Component | Technology Used |
|------------|----------------|
| Programming Language | Python 3 |
| Frontend / UI | Gradio |
| Backend | OpenAI GPT-4 (or fallback generator) |
| Database | SQLite (Simulated data storage) |
| Security | `cryptography.Fernet` for encryption |
| Environment | Google Colab |

---

## 🧩 Prompt Design

### 🎛️ System Prompt
```
You are TalentScout's AI Hiring Assistant. 
Collect candidate information (name, contact, experience, desired role, location, tech stack) and generate 3–5 technical questions for each declared technology. 
Maintain a polite, professional tone and end the chat gracefully when the user types 'end', 'bye', or 'exit'.
```

### 🎯 Technical Question Generation Prompt
```
Generate 3–5 concise technical interview questions for the technology: {tech}.
Candidate experience: {years} years.
Position applied: {position}.
Output format: numbered list of short questions (no answers).
```

### 💬 Example Conversation
```
👋 Hi, I’m TalentScout Hiring Assistant! Please tell me your full name.
> Hi I am Sornambal
Nice to meet you, Sornambal! Please provide your email address.
> email: sornambal@gmail.com
Email saved. Please provide your phone number.
> phone: +919876543210
Great! How many years of experience do you have?
> 3
Got it — 3 years of experience noted. What position are you applying for?
> Python Developer
Understood. Where are you currently located?
> Chennai
Thanks! What’s your tech stack?
> tech: Python, Django
✅ Tech stack saved: Python, Django.
I’ve generated questions. Type 'show' to view them.
```

---

## 💾 Data Handling & Privacy

- Candidate data is **simulated** and stored locally in `talentscout.db`.  
- Sensitive fields (Name, Email, Phone) are **encrypted** using `Fernet` before saving.  
- Tech stack and generated questions are stored as JSON.  
- No real candidate data or external API logs are collected.

---

## 🧩 Installation & Usage

### 🧠 Requirements
- Python 3.10+
- Google Colab or local Jupyter environment
- OpenAI API key (optional — fallback generator works offline)

### 📦 Install Dependencies
```bash
!pip install gradio openai cryptography
```

### 🔑 Set API Key (optional)
```python
import os
os.environ["OPENAI_API_KEY"] = "sk-xxxxxxxxxxxxxxxx"
```

### ▶️ Run the App
```python
!python app.py
```
Or in Colab:
```python
app.launch(share=True)
```

### 💬 Usage Steps
1. Run all notebook cells in order.  
2. Enter your OpenAI key (optional).  
3. Chat through the Gradio interface.  
4. Provide candidate info and tech stack.  
5. Type `show` to view generated questions.  
6. Type `end` to finish — the bot saves your responses securely.

---

## 🧠 Technical Details

| Module | Description |
|---------|--------------|
| `validate_email()` / `validate_phone()` | Input validation helpers |
| `generate_questions()` | Calls GPT-4 or fallback generator |
| `handle()` | Manages conversation flow |
| `reset()` | Resets chatbot session |
| `save_candidate()` | Encrypts and saves user data to SQLite |
| `fallback_questions()` | Default question generator without API |

---

## 📊 System Design Overview

```
+------------------------+
|  Gradio Chat UI        |
|  (Frontend)            |
+-----------+------------+
            |
            v
+------------------------+
|  handle() Logic        |
|  (State Management)    |
+-----------+------------+
            |
            v
+------------------------+
|  LLM / Fallback        |
|  (generate_questions)  |
+-----------+------------+
            |
            v
+------------------------+
|  SQLite + Encryption   |
|  (Data Storage)        |
+------------------------+
```

---

## 💬 Example Generated Output

**Tech Stack:** Python, Django  
**Generated Questions:**
```
Python:
1. Explain Python decorators.
2. What is the difference between a list and a tuple?
3. How does Python manage memory?

Django:
1. What are Django middleware and how are they used?
2. Explain Django ORM and query optimization.
3. What is the purpose of migrations in Django?
```

---

## 🧩 Challenges & Solutions

| Challenge | Solution |
|------------|-----------|
| Maintaining chat context | Used session dictionary to track fields |
| Handling invalid input | Implemented regex + fallback prompts |
| API failure or missing key | Added fallback static generator |
| PII storage security | Used `Fernet` encryption for sensitive data |
| Smooth exit flow | Added end keywords + polite summary |

---

## 🧠 Optional Enhancements (Bonus)

- **Sentiment Analysis:** Detect candidate tone during chat  
- **Multilingual Support:** Translate user messages using `langdetect`  
- **Cloud Deployment:** Streamlit Cloud / Hugging Face Spaces  
- **Recruiter Dashboard:** View saved candidate info & questions  

---

## 🎥 Demo Instructions (for Loom / Submission)

1. Start your Colab notebook.  
2. Record with Loom:  
   - Greeting → Info Collection → Tech Stack → “show” Questions → “end” → Save.  
3. Keep video under 2 minutes.  
4. Include video link in your submission portal.

---

## 🧾 Submission Checklist

| Deliverable | Description | Status |
|--------------|-------------|---------|
| ✅ Source Code | Complete chatbot in Colab | ✅ |
| ✅ Working Demo | Gradio chat tested successfully | ✅ |
| ✅ README.md | Complete documentation | ✅ |
| ✅ Secure Storage | SQLite + Encryption | ✅ |
| ✅ Optional Demo Video | Loom / Gradio link | ✅ |

---

## 📜 References

- [Streamlit Docs](https://docs.streamlit.io/)  
- [Gradio Documentation](https://gradio.app/docs/)  
- [OpenAI API Reference](https://platform.openai.com/docs/)  
- [Prompt Engineering Guide](https://www.promptingguide.ai/)  
- [GDPR Privacy Principles](https://gdpr.eu/)

---

## 🏁 Conclusion

This project successfully demonstrates how **LLMs** can automate **technical candidate screening** while maintaining data privacy and conversational flow.  
It aligns with the **AI/ML Intern Assignment** objectives — showcasing prompt design, context handling, and secure AI-powered automation.
