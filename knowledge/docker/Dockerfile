FROM python:3
COPY . /app
WORKDIR /app
RUN pip install knowledge-repo[all]
RUN pip install --upgrade requests psycopg2 requests_oauthlib flask_login flask_principal
RUN apt-get update && apt-get install -y cron
ADD crontab /etc/cron.d/kr-cron
RUN chmod 0644 /etc/cron.d/kr-cron
RUN chmod +x /app/git-clone.sh

RUN touch /var/log/cron.log
CMD cron && tail -f /var/log/cron.log

CMD bash start.sh
