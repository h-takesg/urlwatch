# ここは
webページの監視を行うdocker-compose
中身はurlwatch

# 仕様
15分に一回見に行く

# 使い方
## 監視対象の設定
`data/urls.yaml`を編集する

`urlwatch --test-filter 1`で1つ目の監視対象をテストできる

## 通知先を設定する
例えばslack
```
// urlwatch.yaml
  slack:
    enabled: true
    max_message_length: 40000
    webhook_url: 'https://api.slack.com/...'
```

# 設定
## 監視間隔
cronで管理されている
`data/crontab`を書き換えればよい
一部だけ別間隔にしたければ参照する`urls.yaml`を複数作り，オプションを変える

## 更新がなくても通知を投げる
```
// urlwatch.yaml
  unchanged: true
```
設定確認に便利
