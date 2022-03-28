# Flask app build
FROM python:3.9.12-alpine as base

# Upgrade pip. Just a best practice to keep pip up to date.
RUN python3 -m pip install --upgrade pip

# System packages required for installing psutils pip package
RUN apk update && apk add gcc \
                    libc-dev \
                    linux-headers

# Switch to app dir
WORKDIR /app

# Copy requirements.txt
COPY ./requirements.txt ./requirements.txt

# Install python packages
RUN python3 -m pip install -r requirements.txt

# Copy other files
COPY . .

# Run flask app using gunicorn
ENTRYPOINT ["./gunicorn.sh"]