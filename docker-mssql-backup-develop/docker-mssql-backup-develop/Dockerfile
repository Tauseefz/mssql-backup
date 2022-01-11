FROM mcr.microsoft.com/mssql-tools:latest
LABEL MAINTAINER="BBT Software AG <opensource@bbtsoftware.ch>"

ENV DB_SERVER="mssql" \
    DB_USER="SA" \
    DB_PASSWORD="" \
    DB_NAMES="" \
    AZ_USERNAME="" \
    AZ_PASSWORD="" \
    AZ_STORAGEACCOUNT="" \
    AZ_FILESHARE="" \
    BACKUP_CLEANUP=false \
    BACKUP_AGE=7 \
    SKIP_BACKUP_LOG=false \
    PACK="" \
    ZIP_PASSWORD="" \
    PUSH_REMOTE_MODE="" \
    MAIL_TO=""    

RUN apt-get update && \
    apt-get install -y cron zip msmtp msmtp-mta mailutils && \
    rm -rf /var/cache/apk/*

COPY backup.sh /usr/local/bin/
RUN chmod +x /usr/local/bin/backup.sh

COPY docker-entrypoint.sh /usr/local/bin/
RUN chmod +x /usr/local/bin/docker-entrypoint.sh
ENTRYPOINT ["docker-entrypoint.sh"]
