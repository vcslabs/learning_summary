## SAM(Serverless Application Model)
### template.md
* template.yaml は AWS CloudFormation テンプレートとして機能するファイルです。このファイルには、デプロイするサーバーレスアプリケーションのアーキテクチャとリソースを定義します。
<br>具体的には以下のような要素を含むことができます：
  * Lambda関数: コードの場所、ランタイム、ハンドラー、環境変数などの設定。
  * API Gateway: ルート、メソッド、セキュリティ設定など。
  * DynamoDBテーブル: 主キー、読み書き容量ユニット、ストリーム設定など。
  * その他のリソース: SAM/CloudFormationでサポートされる他のAWSリソース。
  * イベントソースマッピング: Lambda関数をトリガーするためのイベントソース（例: S3バケットの変更、DynamoDB Stream、SNSトピックなど）。
### samconfig.toml
* samconfig.toml は、sam deploy コマンドのデフォルトのパラメータ値を提供する設定ファイルです。ガイド付きデプロイモード (sam deploy -g) を使用すると、このファイルが生成され、後続のデプロイで使用されるパラメータのデフォルト値が保存されます。
<br>このファイルには以下のような情報が含まれることがよくあります：
  * デプロイするCloudFormationスタックの名前
  * 使用するS3バケット
  * デプロイするリージョン  
  * CloudFormationの変更セットを確認するかどうか
  * その他、sam deploy コマンドのための追加パラメータ
* これらにより、sam deploy を再度実行する際に、毎回同じパラメータを手動で入力する必要がなくなります。