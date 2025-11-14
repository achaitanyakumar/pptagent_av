install git hub repo
cd pptagent_av-main

then create virtual environment
activate it -source .venv/bin/activate

install uv
uv sync

install mineru

then we need three terminal 
1.to run mineru-api
2.backend
3.frontend


before this run source .env
which contains api keys of language ,image and mineru port number to backend
like this 
.env file
export VISION_MODEL="Qwen/Qwen2.5-VL-7B-Instruct"
export VISION_API_BASE=""   
export huggingfaceKey=""                                see-- model_utils.py 

export MINERU_API="http://localhost:8000/file_parse"

export API_BASE=""
export LANGUAGE_MODEL=""
export GROQ_API=""


mineru-api --host 0.0.0.0 --port 8000
python3 pptagent_ui/backend.py
 npm run serve-    in cd pptagent_ui

outputs-
has default reference ppt 
https://drive.google.com/drive/folders/1ZU9UI3LjHV6xnoBERUbrzzAVLG7lYF2y?usp=sharing

before running add default reference ppt files in runs and change default file in backend.py 


