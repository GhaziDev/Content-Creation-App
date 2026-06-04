FROM python:3.13-alpine AS base
RUN apk add --no-cache gcc musl-dev postgresql-dev libffi-dev
WORKDIR /backend
COPY requirements.txt .
RUN python -m pip install --no-cache-dir -r requirements.txt
RUN python -m pip install -r requirements.txt


FROM base AS server
WORKDIR /backend
COPY . .
EXPOSE 7000
CMD python manage.py migrate && gunicorn backend.wsgi:application --bind 0.0.0.0:7000
