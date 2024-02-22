from python:3.9
WORKDIR /app
COPY app.py .
COPY prompt-back.txt /
RUN pip install flask flask_cors
expose 5000
CMD ["flask", "run", "--host=0.0.0.0"]