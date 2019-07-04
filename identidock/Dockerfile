FROM python:3.7.3

RUN apt-get update
# ユーザ追加
RUN groupadd -r uwsgi && useradd -r -g uwsgi uwsgi
RUN apt-get install python3-pip -y
RUN pip3 install Flask
RUN pip3 install uWSGI
RUN pip3 install requests
RUN pip3 install redis

WORKDIR /app
COPY app /app
COPY cmd.sh /

# 外部公開するポートを指定。これだけだとホストから参照できない。コンテナ起動時のオプションでホスト側のポートにバインドする。
EXPOSE 9090 9191
USER uwsgi

# CMD ["uwsgi", "--http", "0.0.0.0:9090", "--wsgi-file", "/app/identidock.py", "--callable", "app", "--stats", "0.0.0.0:9191"]
CMD ["/cmd.sh"]



