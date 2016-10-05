# logstash + elasticsearch + kibanaの動作確認

お手軽にapcheのアクセスログを可視化。

## Ansibleで環境構築

Vagrant + ansibleで環境を構築します。

レシピ作成時のバージョン

    Vagrant 1.8.1
    ansible 2.1.1.0

コマンド

    # vagrant up -d
    # ansible-playbook -i hosts site.yml

## 動作確認

httpアクセス

    http://192.168.33.10/

kopfにアクセス

    http://192.168.33.10:9200/_plugin/kopf/

kibanaにアクセス

    http://192.168.33.10:5601/

kibanaの初期画面は「Configure an index pattern」の画面ですがhttpアクセスしてログ出力されていればそのままcreateで問題無いです。

「Discover」でグラフが表示されない場合、右上の時計アイコンから時間をいじれば表示されます。

## 備考

起動停止

    sudo service kibana
    sudo service elasticsearch
    sudo service logstash

logstash設定ファイルのチェック

     sudo /etc/init.d/logstash configtest

# 参考サイト

* [15分で作る、Logstash＋Elasticsearchによるログ収集・解析環境](http://knowledge.sakura.ad.jp/tech/2736/)

* [Logstashを利用したApacheアクセスログのインポート](http://blog.johtani.info/blog/2014/11/21/import-apache-accesslog-using-logstash/)

* [Logstashのインストールと簡単な設定方法](http://symfoware.blog68.fc2.com/blog-entry-1910.html)

* [Fluentd + Elasticsearch + Kibanaで遊んでみた(その3) 〜家計簿データのKibana 4での可視化まで〜](http://totech.hateblo.jp/entry/2016/01/07/114252)
