# Nmap 簡易ポートスキャンツール（CSV出力）

## 概要
   改行区切りのサーバ一覧ファイルを基にnmap でポートスキャンを実施しCSV形式で表示します。  
   通常nmapコマンドでは、xml形式の出力しかサポートしていないので、  
   このツールを作りました。


## インストール

   1. 実施には、nmapコマンドが必要です。
   ```
   #CentOS
   sudo yum install nmap
   #ubuntu
   sudo apt-get install nmap
   ```

   1. このツールをダウンロードします。
   ```
   git clone https://github.com/iiyuda7/nmap_easy_port_scan.git
   ```
   
## 実行例


1. ポートスキャン対象のリストを作成します。
   ```
   echo '192.168.1.1' >> hoge.list
   echo '192.168.1.2' >> hoge.list
   echo '192.168.1.3' >> hoge.list
   ```

1. ポートスキャンを実行します。
   実行には、root権限が必要です。（UDPのスキャンを行うため)
   また、UDPのスキャンも実施しているので、結構時間がかかりますので、気長に待ちます。

   ```
   sudo sh portcheck.sh hoge.list > result.csv
   ```

1. 実行結果は標準出力にCSV形式で出力されます。
   必要に応じて、ファイルにリダイレクトすると良いでしょう。

## 備考
   XML を CSV形式にするのにnmap-parser-xml-to-csv という、モジュールを利用しています。 
   ただし、こちらでは、TCP/UDPの表示ができないため、修正したコードをプルリクエスト中。 
   マージしてもらえたら、そっちを直接使うように修正する予定です。 
　 マージまでの間は、修正版をこのレポジトリに梱包する形で利用しています。

  - [nmap-parser-xml-to-csv](https://github.com/materaj/nmap-parser-xml-to-csv)
  - [nmap-parser-xml-to-csv_PR](https://github.com/materaj/nmap-parser-xml-to-csv/pull/2)

