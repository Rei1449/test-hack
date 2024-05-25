FROM python:3.9-slim AS build

WORKDIR /app/backend

COPY requirements.txt /app/backend/requirements.txt
RUN pip install --no-cache-dir --upgrade -r /app/backend/requirements.txt

# 開発用環境
FROM python:3.9-slim AS dev

COPY --from=build /usr/local/lib/python3.9/site-packages /usr/local/lib/python3.9/site-packages
COPY --from=build /usr/local/bin /usr/local/bin

WORKDIR /app/backend

COPY src /app/backend/src

CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8080"]
