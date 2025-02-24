
## **📞 Sales Caller AI - Twilio + AI Voice Assistant**
### **🚀 AI-powered sales assistant for real-time customer calls!**
This project uses **Flask, Twilio, and Mistral-7B AI** to make **real-time sales calls** to Indian numbers, provide course details, and book Google Meet demos.

![Twilio AI Caller](https://img.shields.io/badge/Twilio-Voice%20AI-red)  
![Flask](https://img.shields.io/badge/Flask-Web%20Server-blue)  
![Hugging Face](https://img.shields.io/badge/HuggingFace-Mistral--7B-yellow)  

---

## 📌 **Project Features**
✅ **AI-Powered Sales Calls** – Calls real users & interacts with AI.  
✅ **Real-Time Voice Responses** – Uses Twilio for a human-like voice.  
✅ **Interactive IVR System** – Press **1 for course details, 2 for booking a demo**.  
✅ **Automated Google Meet Booking** – AI books a meeting and sends a link.  
✅ **No Manual Updates Required** – ngrok URL is dynamically updated!  

---

## ⚙️ **Tech Stack**
| Technology | Usage |
|------------|-------|
| **Flask** | Web server to handle Twilio voice requests |
| **Twilio API** | Makes real-time calls to Indian numbers |
| **Mistral-7B** | AI model for generating responses |
| **Ngrok** | Exposes Flask server to the internet |
| **Python (Transformers)** | NLP & AI Model Handling |

---

## 📂 **Installation & Setup**
### 🔹 **1. Install Dependencies**
```bash
pip install flask twilio transformers accelerate sentencepiece pyngrok
```

### 🔹 **2. Authenticate Hugging Face**
```python
from huggingface_hub import login
login(token="your_huggingface_token")  # Replace with your actual HF token
```

### 🔹 **3. Start the AI Model**
```python
from transformers import AutoModelForCausalLM, AutoTokenizer
import torch

model_name = "mistralai/Mistral-7B-Instruct-v0.1"
tokenizer = AutoTokenizer.from_pretrained(model_name, token="your_huggingface_token")
model = AutoModelForCausalLM.from_pretrained(model_name, torch_dtype=torch.bfloat16, device_map="auto")

print("✅ AI Model Loaded Successfully!")
```

### 🔹 **4. Start Flask & ngrok**
```python
from flask import Flask, request
from pyngrok import ngrok

app = Flask(__name__)

ngrok_url = ngrok.connect(5000).public_url
print(f"🌍 ngrok is running at: {ngrok_url}")

@app.route("/voice", methods=["POST"])
def voice():
    return "AI Sales Caller is running!"

app.run(debug=True, port=5000)
```

### 🔹 **5. Make a Call Using Twilio**
```python
from twilio.rest import Client

TWILIO_SID = "your_twilio_sid"
TWILIO_AUTH_TOKEN = "your_twilio_auth_token"
TWILIO_PHONE = "+1234567890"  # Your Twilio number
CUSTOMER_PHONE = "+91XXXXXXXXXX"  # Customer's number

client = Client(TWILIO_SID, TWILIO_AUTH_TOKEN)

call = client.calls.create(
    to=CUSTOMER_PHONE,
    from_=TWILIO_PHONE,
    url=f"{ngrok_url}/voice"
)
print(f"📞 Call initiated: {call.sid}")
```

---

## 🎥 **Demo Video**
📌 [Watch the full AI Caller demo here](#) (Replace with your Google Drive link).  

---

## 📜 **Project Structure**
```
📂 Sales-Caller-AI/
│── Sales Caller AI.ipynb               # Flask Server & AI Model
│── README.md            # Project Documentation

```

---

## 📧 **Contact**
💡 Created by **Kavya Kapoor**  
📧 Email: **kavyakapoor869@gmail.com**  
🚀 **Feel free to contribute or ask questions!**  

---
