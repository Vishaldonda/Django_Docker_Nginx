# Dockerfile
FROM python:3.11.4-slim-bullseye AS BASE

ENV PYTHONUNBUFFERED 1
ENV PYTHONDONTWRITEBYTECODE 1

WORKDIR /app

# Copy all project files into the container
COPY . .

RUN pip install Django

# Set the environment variable for Django settings
ENV DJANGO_SETTINGS_MODULE=myproject.settings

RUN python manage.py collectstatic --noinput
RUN python manage.py makemigrations
RUN python manage.py migrate

# Expose port 8000 for Django
EXPOSE 8000

# Command to run Django (can be replaced if necessary)
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]