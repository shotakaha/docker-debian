# docker-debian

docker compose debian

## イメージ

- https://hub.docker.com/_/debian

## 起動

```console
$ docker compose up -d
[+] Running 2/2
 ✔ Network docker-debian_default     Created
 ✔ Container docker-debian-debian-1  Started
```
## 確認

```console
docker compose ps
NAME                     IMAGE                  COMMAND   SERVICE   CREATED              STATUS              PORTS
docker-debian-debian-1   debian:bookworm-slim   "bash"    debian    About a minute ago   Up About a minute
```

## ログイン

```console
$ docker compose exec debian bash
root@4d928d218c19:/# 

root@4d928d218c19:/# cat /etc/os-release 
PRETTY_NAME="Debian GNU/Linux 12 (bookworm)"
NAME="Debian GNU/Linux"
VERSION_ID="12"
VERSION="12 (bookworm)"
VERSION_CODENAME=bookworm
ID=debian
HOME_URL="https://www.debian.org/"
SUPPORT_URL="https://www.debian.org/support"
BUG_REPORT_URL="https://bugs.debian.org/"
```

## 終了

```console
$ docker compose down
```