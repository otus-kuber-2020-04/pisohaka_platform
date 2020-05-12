FROM python:3.7-alpine3.8

RUN adduser -D -H -u 1001 appuser
RUN mkdir /app && chown -R appuser:appuser /app/
WORKDIR /app
EXPOSE 8000

CMD ["python", "-m", "http.server", "8000"]
