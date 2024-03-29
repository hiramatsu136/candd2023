# 2023年度施策メモ

## 作成するもの
- 会議出欠管理画面のバックエンドアプリ  
  ※イメージとしては、2課スプレッドシートの出欠シートのようなもの
- フロントの仕様に応じて必要なAPIを定義  
- 最終的にはサーバアプリのDocker imageを成果物とする  
  （開発環境で動作すればOK、デプロイなどは考えなくてよい）

## チームメンバー・担当
仕様がもう少し固まってから担当決め実施予定  
- KO：取りまとめ・雑用（環境用意など）  
- SI：xxx  
- HA：xxx  
- MO：xxx  
- SA：xxx  

### 作業洗い出し
現時点では、大まかに以下の割り振りが考えられる  
- コンテナ周り（イメージ作成・マウント設定など構成の詳細化）
- DB周り（初期化・日付の文字列アクセスなど調査・検証）
- FastAPIの細かい仕様（書き方など）
- HTML配信方法

## システム構成
- 使用技術はPython/FastAPIとする  
- プラットフォームはコンテナ化する都合上Linuxとする  
- データ保存形式はSQLiteを使用する

## IF仕様
- IF仕様叩き台作成  
  →仕様展開済み  
  →フロント/バック間の細かな不整合はフロント側で対応するとのこと  
  →現時点のIF仕様でいったんfixとする  

### IF仕様：要調査事項
- FastAPI本体はHTMLなどの静的コンテンツ配信に対応していない
  →別途プラグインを入れる必要あり  

## DB仕様
- IF仕様案と同時にチーム内で検討済み  
  →社員管理テーブルは持たず、出欠管理の単一テーブルにデータを積み上げる方式とする  
  →同一社員・同一月のリクエストが来たらUPDATE、それ以外はINSERT（いわゆるUPSERT）  

### DB仕様：要調査事項
- 年月を文字列で扱っているので、もしorder byが正常に動作しないようならdatetimeに変更する必要あるかも  
  （半角文字のみ、かつ0埋めで桁数揃えているので大丈夫だとは思う）  
  ★要調査
- connectでDB作成してくれるが、文字コード・タイムゾーンなどの初期設定も同時に可能か？  
  connectに設定用の引数などが無いなら、別途設定用の処理を調べて叩くか、  
  運用として事前に設定入れておく必要あり（DB初期設定が必要になる）  
  ★要調査

## 開発環境接続手順展開  
- 10月に展開済み  
  →1月打ち合わせにて全員で接続確認予定  
  →メンバーが揃わなかった場合、日時を指定して個々で接続確認してもらう  
  ※接続先の作業用サーバは普段停止させているため、事前に日時をアナウンスして起動させておく必要あり

## 2月作業予定
- FD（今までの内容）の意識合わせ
- DD執筆・技術検証の役割分担

## その他TODO・メモなど
- 今月～来月までにやること
  - 接続確認未完のメンバーは、日時をメール調整のうえ対応お願いします

