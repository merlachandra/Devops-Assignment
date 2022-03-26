# Flask app build
FROM python:3.9.12-alpine as base

# Upgrade pip
RUN python3 -m pip install --upgrade pip

# Required for installing psutils pip package
RUN apk update && apk add gcc \
                    libc-dev \
                    linux-headers
# Switch to app dir
WORKDIR /app

# Copy requirements.txt
COPY ./requirements.txt ./requirements.txt

#Install python packages
RUN python3 -m pip install -r requirements.txt

COPY . .

# Run flask app using gunicorn
ENTRYPOINT ["./gunicorn.sh"]