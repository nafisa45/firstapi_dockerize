# firstapi_dockerize
I have to run these commands:
1.python3 -m venv env
2.source env/bin/activate
3.pip install fastapi uvicorn
locate virtual environment
4.touch main.py
5.uvicorn main:app --reload --port=8000 --host=0.0.0.0
now go to http://127.0.0.1:8000/ to see raw data and the message.
and go to http://127.0.0.1:8000/docs to see swagger ui
then ctrl+c to stop the server.
6.pip freeze > requirements.txt
7.deactivate
8.docker compose up --build
9.docker compose up

but u have to run just these after downloading:
1.python3 -m venv env
2.source env/bin/activate
3.pip install fastapi uvicorn
locate virtual environment
4.docker compose up
