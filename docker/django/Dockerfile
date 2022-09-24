FROM python:3.9.6-alpine

WORKDIR /usr/src/app

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

RUN apk update

RUN pip install --upgrade pip
COPY ./django_project/requirements.txt .
RUN pip install -r requirements.txt --no-cache-dir

# # copy entrypoint.sh
COPY ./docker/django/entrypoint.sh .
RUN sed -i 's/\r$//g' /usr/src/app/entrypoint.sh
RUN chmod +x /usr/src/app/entrypoint.sh

# copy project
COPY ./django_project .


ENTRYPOINT ["/usr/src/app/entrypoint.sh"]