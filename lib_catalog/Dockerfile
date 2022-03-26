FROM python:3.9-buster
WORKDIR /app
RUN adduser appuser && chown -R appuser /app
USER appuser
COPY requirements.txt /app/requirements.txt
RUN pip install -r requirements.txt
COPY . /app

EXPOSE 8000
CMD ["/bin/bash", "-c", "python manage.py migrate && exec python manage.py runserver 0.0.0.0:8000"]