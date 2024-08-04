# pull official base image
FROM python:3.11-slim-bullseye

# set work directory
WORKDIR /srv/app

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# install dependencies
RUN pip install --upgrade pip
# Corrected path for requirements.txt based on the actual location
COPY ../requirements.txt /srv/app/

RUN apt-get update && apt-get install -y \
  gcc \
  netcat \
  libpq-dev \
  postgresql-client \
  && apt-get clean

# install dependencies from requirements.txt
RUN pip3 install -r requirements.txt

# copy entrypoint.sh from the right location
COPY backend/entrypoint.sh /srv/app/backend/

# copy the rest of the project
COPY . /srv/app/

# Ensure entrypoint.sh is executable
# RUN chmod +x /srv/app/entrypoint.sh
RUN ["chmod", "+x", "/srv/app/backend/entrypoint.sh"]
# run entrypoint.sh
# ENTRYPOINT ["/srv/app/entrypoint.sh"]
