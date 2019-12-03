# Docker + CodeIgniter + VirtualHost

This image serves as a starting point for legacy CodeIgniter projects.  

## Supported Tags

- `latest`: [Dockerfile](https://github.com/hojin-kr/docker-codeigniter-hmvc/blob/master/Dockerfile)

## Quick Start

Start a container using the latest image
docker-compose.yml 파일을 열어서 멀티 컨테이너로 띄울 서비스를 작성합니다. 
000-default.conf 파일에 virtual host 정보를 입력합니다.

```shell
$ vi docker-compose.yml
```

설정을 마쳤으면 최상단 디렉토리에서 도커를 띄워 서비스를 시작합니다.

```shell
$ docker-compose up
```

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
