FROM asarchami/hadoop-base:latest
MAINTAINER Ali Sarchami "ali.sarchami@gmail.com"

HEALTHCHECK CMD cirl -f http://localhost:8088/ || exit 1

ADD run.sh /run.shRUN chmod a+x /run.sh

EXPOSE 8088

CMD ["/run.sh"]
