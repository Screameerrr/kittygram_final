FROM python:3.9

WORKDIR /app

COPY requirements.txt .

RUN pip install --upgrade pip
RUN pip install -r requirements.txt

COPY . .

ENV PYTHONUNBUFFERED=1

EXPOSE 8080

CMD ["gunicorn", "kittygram_backend.wsgi:application", "--bind", "0:8000"]
