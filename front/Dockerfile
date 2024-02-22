FROM python:3.9
WORKDIR /app

# Copier les fichiers d'application dans le répertoire de travail
COPY app.py /app
COPY templates /app/templates

RUN pip install flask requests
EXPOSE 80
CMD ["python3", "app.py"]