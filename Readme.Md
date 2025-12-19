Streaming Flow Explanation

The browser sends a chat request to the FastAPI backend at /api/chat with the conversation history and streaming enabled. The backend optionally checks a LAN token for security, then forwards the request to Ollama’s /api/chat endpoint using a streaming HTTP connection. As Ollama generates its response, it sends newline-delimited JSON chunks containing partial tokens. The backend reads these chunks in real time, extracts the text content, and immediately streams it back to the browser using StreamingResponse. On the frontend, JavaScript reads the incoming stream and appends each chunk to the chat UI, creating a live typing effect. When Ollama finishes, the stream closes and the full response is stored for the next message.

Custom Modelfile Explanation

We create this custom model BarangayBot by building on the llama3.2 base model and configuring it with specific parameters and strict behavioral rules using a Modelfile. The temperature is set to 0.7 to balance clarity and natural responses, while a 4096-token context window allows for multi-turn conversations. A system prompt permanently defines BarangayBot’s role as an official barangay virtual assistant that only handles barangay-related services, documents, and information, with a polite and helpful tone and very light sarcasm. The model is hard-coded with official document types, exact fees, and processing times to ensure consistent, accurate answers without placeholders. Strict rules enforce that the assistant must refuse all non-barangay inquiries using a single exact message, without explanations or variations, guaranteeing controlled, predictable, and domain-focused responses.

Instruction

Ensure that you install python 3.13 and follow the instruction

    
Setup  enviroment      
        paste it in the terminal 1 - python -m venv .venv
                                 2 - .venv/Scripts/pip install ollama 

Active the venv
            paste it in the terminal 1 - Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
                                     2 - .\.venv\Scripts\Activate.ps1

Install the dependencies
            paste it in the terminal - python -m pip install fastapi "uvicorn[standard]" httpx

Open new terminal
        run this in the terminal 1 - python -m uvicorn server:app --host 0.0.0.0 --port 3000

Open another terminal
        run this in terminal 2 - python -m http.server 5500

Access this on chrome
       copy this and paste in chrome - http://localhost:5500/index.

       
       
if you already install the dependencies to run this

Open new terminal
        run this in the terminal 1 - python -m uvicorn server:app --host 0.0.0.0 --port 3000

Open another terminal
        run this in terminal 2 - python -m http.server 5500

Access this on chrome
       copy this and paste in chrome - http://localhost:5500/index.html