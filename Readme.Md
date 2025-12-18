Instruction
    
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
       copy this and paste in chrome - http://localhost:5500/index.html