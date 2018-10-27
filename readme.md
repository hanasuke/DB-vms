# DB-VMくん
## なんこれ

CentOS7のVMにPostgreSQLとRedisを突っ込んで、ホストマシンからアクセスできるくん。
これを入れることで、ホストマシンのDBを汚す必要がなくなります。
以下のものを突っ込んでいます。

- PostgreSQL 9.6.x
- Redis 3.2.x


## Vagrant版
### 起動方法

```
$ vagrant up
$ ansible-playbook site.yml
```

### 使い方

ホストマシンとプライベートネットワークを作っています。
IPアドレスは`192.168.100.2`です。
ホストマシンからCLIで利用するときはホストマシンにライブラリを入れておく必要があります。

#### PostgreSQL

CLIの場合、ホストマシンから以下のコマンドで接続できます。

```
$ psql -h 192.168.100.2 -U vagrant
```

#### Redis

CLIの場合、ホストマシンから以下のコマンドで接続できます。

```
$ redis-cli -h 192.168.100.2
```

## docker-compose版
### 起動方法
```
docker-compose up
```

### 使い方
#### postgresql
```
$ psql -h localhost -p 15432
```

#### redis

```
redis-cli -h localhost -p 16379
```

# 余談

設定でランダマイズを有効にしているので、`cowsay`を入れておくと楽しいことになります。
