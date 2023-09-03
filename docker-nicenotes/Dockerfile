FROM python:3

# Create app directory
WORKDIR /app

# Install app dependencies
COPY requirements.txt ./

# RUN apk add libxml2-dev libxslt-dev python-dev

RUN pip install -r requirements.txt


CMD [ "python" ]
