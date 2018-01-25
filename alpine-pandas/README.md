# alpine で pandas 使えるようにしたやつ

AWS Code build に乗せてバッチ処理する用のBASEコンテナ
Lambda で処理するにも 5分で終わらないとか、メモリ足りないとかあるので
S3にファイル配置 -> λ -> Codebuildで 渡されたCSVのETLを行う
GlueのSparkで分散するほどでも無いし、かといってλで終わる範囲でもない
って場合用
数GのCSVまでならこれで処理できるはーずー

