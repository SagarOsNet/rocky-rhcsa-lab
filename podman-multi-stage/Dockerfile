FROM python:3.12-alpine AS builder
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir --target=/install -r requirements.txt
COPY app.py .

FROM python:3.12-alpine
WORKDIR /app
COPY --from=builder /install /usr/local/lib/python3.12/site-packages
COPY --from=builder /app/app.py .

EXPOSE 8080
CMD ["python", "-m", "flask", "run", "--host=0.0.0.0", "--port=8080"]
