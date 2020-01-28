# Docker + CodeIgniter + VirtualHost

This image serves as a starting point for legacy CodeIgniter projects.  

## Supported Tags

- `latest`: [Dockerfile](https://github.com/hojin-kr/docker-codeigniter-virtualhost/blob/master/Dockerfile)

## Quick Start

깃 저장소를 클론 받습니다.

```shell
$ git clone https://github.com/hojin-kr/docker-codeigniter-virtualhost.git
```

000-default.conf 파일에 virtual host 정보를 수정합니다.

```shell
$ vi 000-default.conf
```
  
Container를 빌드합니다.

```shell
$ docker build -t hojindev/codeigniter-virtualhost .
```

코드이그나이터 루트 디렉토리에 docker-compose.yml을 복사하고 도커를 띄웁니다.

~~~
# docker-compose.yml
version: '2.2'
services:
  web:
    image: hojindev/codeigniter-virtualhost
    ports:
     - 80:80
    volumes:
      - $PWD:/var/www/html/
~~~

or

데이터베이스까지 함께 설치
~~~
# docker-compose.yml
version: '2.2'
services:
  web:
    image: hojindev/codeigniter-virtualhost
    ports:
     - 80:80
    volumes:
      - $PWD:/var/www/html/
  db:
    image: mysql:5.7
    ports:
      - 3306:3306
    environment:
      - MYSQL_ALLOW_EMPTY_PASSWORD=true
    volumes:
      - $PWD/../mysql_dev:/var/lib/mysql

~~~

```shell
$ docker-compose up
```  

## 변경 사항
    - mysql, mysqli 둘다 설치
    - session.auto_start = 1

### Environment Variables

Environment variables can be passed to docker-compose.

The following variables trigger actions run by the entrypoint script at runtime.

| Variable | Default | Action |
| -------- | ------- | ------ |
| ENABLE_CRON | false | `true` starts a cron process within the container |
| FWD_REMOTE_IP | false | `true` enables remote IP forwarding from proxy (Apache) |
| PHP_DISPLAY_ERRORS | off | Override value for `display_errors` in docker-ci-php.ini |
| PHP_POST_MAX_SIZE | 32M | Override value for `post_max_size` in docker-ci-php.ini |
| PHP_MEMORY_LIMIT | 128M | Override value for `memory_limit` in docker-ci-php.ini |
| PHP_UPLOAD_MAX_FILESIZE | 32M | Override value for `upload_max_filesize` in docker-ci-php.ini |
| TZ | UTC | Override value for `data.timezone` in docker-ci-php.ini |

### original git
[https://github.com/aspendigital/docker-codeigniter](https://github.com/aspendigital/docker-codeigniter)
