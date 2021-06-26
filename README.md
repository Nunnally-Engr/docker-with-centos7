# docker-with-centos7

- WEBサーバ構築用Docker
- 静的サイトをWEBサーバにFTPでアップロードして確認するのが面倒だったので作成

## Version
***

- CentOS 7.9
- Apache 2.4.6

## 構築手順
***

### 1. Docker build
```
docker-compose build --no-cache
```

## 静的サイト確認手順
***

### 1. distディレクトリ削除 `※ 初めて確認する時は不要`

```
rm -r dist
```

### 2. 動かしたい静的ファイルを、distディレクトリにコピーする


```bash
# ---------------------------------
# ex. 以下のディレクトリ構成の場合
#
# ~/develop $ tree -L 2
# .
# ├── docker-with-centos7
# │   ├── README.md
# │   ├── apache
# │   ├── docker
# │   └── docker-compose.yml
# ├── sample-web ← コピー元
# │   └── dist
# ---------------------------------

cp -r ../sample-web/dist dist
```

### 3. Docker 起動
```
docker-compose up
```

### 4. ブラウザで、 `http://localhost:3001/` にアクセス

## その他設定
***

### 1. ポート指定方法

- docker-compose.yml
```yaml:docker-compose.yml
    ports:
      - 3001:3001
```

- apache/httpd.conf
```properties:httpd.conf
Listen 3001
```