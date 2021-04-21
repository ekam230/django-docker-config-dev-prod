FROM python:3.8.3-alpine

#set work dir
WORKDIR /usr/src/app

#set env variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONBUFFERED 1


# install psycopg2 dependencies
RUN apk update \
    && apk add postgresql-dev gcc python3-dev musl-dev

#instal dependecies
RUN pip install --upgrade pip
RUN pip install pipenv
COPY ./Pipfile ./
COPY Pipfile.lock ./

RUN set -ex && pipenv install --deploy --system

# copy entrypoint.sh
COPY ./entrypoint.sh .

#copy proj
COPY . .

# run entrypoint.sh
ENTRYPOINT ["/usr/src/app/entrypoint.sh"]
