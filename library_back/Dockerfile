FROM python:3-alpine
WORKDIR /app
COPY ./ ./
RUN apk add --no-cache postgresql-libs
RUN apk add --no-cache --virtual .build-deps gcc musl-dev postgresql-dev
RUN apk add --update --no-cache --virtual .tmp-build-deps \
    gcc libc-dev linux-headers postgresql-dev \
    && apk add libffi-dev
RUN python3 -m pip install -r requirements.txt
EXPOSE 8000
CMD python3 manage.py makemigrations ; python3 manage.py migrate ; python3 manage.py runserver 0.0.0.0:8000