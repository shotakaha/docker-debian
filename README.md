# docker-debian

docker compose debian

## イメージ

- https://hub.docker.com/_/debian

### バージョン

| version | codename | released |
|---|---|---|
| 10 | buster | 2019-07-06 |
| 11 | bullseye | 2021-08-14 |
| 12 | bookworm | 2023-06-10 |

- DebianのコードネームはToy Storyの登場人物（おもちゃ）の名前だそうです

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

## 接続

```console
$ docker compose exec debian bash
root@4d928d218c19:/# 
```

`docker compose exec`で起動したコンテナに接続できます。
上記のサンプルでは、接続後に`bash`を起動しています。

```console
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

コンテナの中は、通常のLinux（Debian）のようにコマンドを使用できます。
上記のサンプルでは、`/etc/os-release`の内容を表示しOSのバージョンを確認しています。

## 終了

```console
$ docker compose down
[+] Running 2/2
 ✔ Container docker-debian-debian-1  Removed
 ✔ Network docker-debian_default     Removed
```

## エラー

```console
$ docker compose exec debian bash
service "debian" is not running
```

起動していないコンテナに接続するとエラーになります。
`docker compose up -d`してコンテナが起動したことを確認してから、`docker compose exec`を実行します。
