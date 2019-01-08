FROM python:3.6.5-alpine

RUN apk update && \
    apk add --virtual build-deps gcc python-dev musl-dev &&\
    apk add --no-cache \
    postgresql-dev \
    netcat-openbsd

WORKDIR /usr/src/app

COPY Pipfile /usr/src/app/Pipfile
COPY Pipfile.lock /usr/src/app/Pipfile.lock

RUN pip install pipenv && pipenv install --dev --system


COPY ./entrypoint.sh /usr/src/app/entrypoint-prod.sh
RUN chmod +x /usr/src/app/entrypoint-prod.sh

COPY . /usr/src/app

CMD ["/usr/src/app/entrypoint-prod.sh"]

