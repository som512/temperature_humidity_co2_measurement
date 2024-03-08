# temperature_humidity_co2_measurement
## ファイル構成
temperature_humidity_co2  
  |-temperature_humidity_co2.ino : Arduino(EPS32)用のプログラム。温湿度センサーとCO2センサー付き。  
IoTserver  
  |-app.py : Flaskサーバー  
  |-data60.pickle : 過去60分間の温湿度とCO2濃度のデータ  
  |-templates  
  |  |-base.html : 他ページでも使いまわす部分(head,header,footer)を格納  
  |  |-index.html : ホームページ  
  |-static  
  |  |-css  
  |  |  |-style.css  
  |  |-images  
  |  |  |-co60.png : 過去60分間のCO2濃度の図、app.py内でアクセスがあると新たに作成する  
  |-instance  
    |data.db : SQLAlchemyのデータ  

## 概要
温湿度センサーとCO2濃度センサーを搭載したArduinoと外部公開していないLAN内のサーバーを、http通信で繋ぎ、LAN内から自室の温湿度とCO2濃度をモニター出来るようにした。
サーバーに記録をPythonだけで疑似的にSQLが使えるSQLAlchemy形式で保存してあり、過去60分とIoTと通信を始めた時からの記録が見れる。
記録が自動更新されていく。
また、過去60分のCO2濃度に関しては図を作成して推移を視覚的に理解可能にした。これによりエラー値、急上昇、急降下などの判定を視覚的に出来る。
図もアクセスの度に自動更新されていく。

## サンプル
![サンプル](./sample.png "サンプル)
