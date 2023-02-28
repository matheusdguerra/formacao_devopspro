FROM python:3.8

WORKDIR /app

COPY requirements.txt requirements.txt

RUN python3 -m pip install --upgrade pip && pip install -r requirements.txt

COPY . .

CMD ["gunicorn", "--bind", "0.0.0.0:5000", "-c", "config.py", "app:app"]