FROM python:3.6.8
#PACOTE REQUER PYTHON 3.6.X
#user/password

ENV PYTHONDONTWRITEBYTECODE=1
#Instalando pacotes necessários
ENV PYTHONUNBUFFERED=1
RUN apt install -y git
RUN git clone https://github.com/rrmmbmg/yowsup.git .
RUN python -m pip install --upgrade pip
RUN python -m pip install -r requirements.txt
WORKDIR /app
RUN adduser -u 5678 --disabled-password --gecos "" appuser && chown -R appuser /app
USER appuser
USER root