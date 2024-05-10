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
and now in case of adding new server:

version: '3'

services:
  post_server:
    build: ./post-server
    command: sh -c "uvicorn main:app --reload --port=8000 --host=0.0.0.0"
    env_file:
      - ./post-server/.env
    ports:
      - "8000:8000"  # Expose port 8000 for the post_server service
    volumes:
      - ./post-server:/app

  notification_server:
    build: ./notification-server
    command: sh -c "uvicorn main:app --reload --port=8080 --host=0.0.0.0"
    env_file:
      - ./notification-server/.env
    ports:
      - "8080:8080"  # Expose port 8080 for the notification_server service
    volumes:
      - ./notification-server:/app
