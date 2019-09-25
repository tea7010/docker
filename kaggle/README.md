### コンテナ作成時のコマンドメモ

1. kaggle APIのtokenを同一フォルダ内におく
1. kaggle APIでDLするコンペを変更
1. 解凍するzipファイルを変更
1. buildして、runする
```
docker run --runtime=nvidia -it -p 8888:8888 --name='{container_name}' -v $(host):/workspace/host {image_name}
```

* docker-composeすればこのあたりのメモもymlに記述できるが、AzureのDataScienceVMのdocker verが古いようなので未実施
