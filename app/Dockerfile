FROM python:3.12-slim as builder

WORKDIR /tmp
COPY . .
RUN pip install -r requirements.txt -t site-packages
RUN pip install pytest
ENV PYTHONPATH=/app/site-packages
RUN pytest

FROM python:3.12-slim
WORKDIR /app
COPY --from=builder /tmp/site-packages ./site-packages
COPY app.py .
ENV PYTHONPATH=/app/site-packages

CMD ["python3", "app.py"]