
FROM python:3.9-slim

ENV PORT=8000

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        libgl1 \
        libglib2.0-0 \
        libsm6 \
        libxext6 \
        libxrender-dev \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /Api

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

RUN pip install python-multipart

COPY Model/1 /Api/Model/1

COPY main.py .

EXPOSE 8000

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
