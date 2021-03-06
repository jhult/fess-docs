==================
JSONによる検索結果
==================

JSON応答による検索
==================

|Fess| の検索結果をJSONにより出力することができます。JSONにより出力するためには管理画面のクロール全般の設定でJSON応答を有効にしておく必要があります。

リクエスト
----------

JSONにより出力結果を得るためには
``http://localhost:8080/fess/json?query=検索語``
のようなリクエストを送ります。リクエストパラメータについては以下の通りです。

+----------------+------------------------------------------------------------------------------------------+
| query          | 検索語。URLエンコードして渡します。                                                      |
+----------------+------------------------------------------------------------------------------------------+
| start          | 開始する件数位置。0から始まります。                                                      |
+----------------+------------------------------------------------------------------------------------------+
| num            | 表示件数。デフォルトは20件です。100件まで表示できます。                                  |
+----------------+------------------------------------------------------------------------------------------+
| fields.label   | ラベル値。ラベルを指定する場合に利用します。                                             |
+----------------+------------------------------------------------------------------------------------------+
| callback       | JSONPを利用する場合のコールバック名。JSONPを利用しない場合は指定する必要はありません。   |
+----------------+------------------------------------------------------------------------------------------+

Table: リクエストパラメータ


レスポンス
----------

以下のようなレスポンスが返ります。

::

    {
        "response": {
            "version": 1,
            "status": 0,
            "query": "\u30C6\u30B9\u30C8",
            "execTime": 0.59,
            "pageSize": 20,
            "pageNumber": 1,
            "recordCount": 101,
            "pageCount": 6,
            "result": [
                {
                    "site": "speedtest.goo.ne.jp\u002F",
                    "contentDescription": "goo \u306E\u63D0\u4F9B\u3059\u308B\u30B9\u30D4\u3C..",
                    "host": "speedtest.goo.ne.jp",
                    "lastModified": "1284739487873",
                    "cache": "\u9FA0-->\n<meta http-equiv=\u0022Content-Type\u0022 content=\..",
                    "score": "4.98744",
                    "digest": "goo \u306E\u63D0\u4F9B\u3059\u308B\u30B9\u30D4\u30FC\u30C9<em>..",
                    "tstamp": "1284739487887",
                    "url": "http:\u002F\u002Fspeedtest.goo.ne.jp\u002F",
                    "id": "http:\u002F\u002Fspeedtest.goo.ne.jp\u002F;type=au,docomo,pc,softbank",
                    "mimetype": "text\u002Fhtml",
                    "title": "\ngoo \u30B9\u30D4\u30FC\u30C9\u30C6\u30B9\u30C8\n",
                    "contentTitle": "\ngoo \u30B9\u30D4\u30FC\u30C9\u30C6\u30B9\u30C8\n",
                    "boost": "1.0",
                    "contentLength": "17810",
                    "urlLink": "http:\u002F\u002Fspeedtest.goo.ne.jp\u002F"
                },
    ...
            ]
        }
    }

各要素については以下の通りです。

+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| response             | ルート要素。                                                                                                                              |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| version              | フォーマットバージョン。                                                                                                                  |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| status               | レスポンスのステータス。status値は、0:正常、1:検索エラー、2または3:リクエストパラメータエラー、9:サービス停止中、-1:API種別エラーです。   |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| query                | 検索語。                                                                                                                                  |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| execTime             | 応答時間。単位は秒。                                                                                                                      |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| pageSize             | 表示件数。                                                                                                                                |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| pageNumber           | ページ番号。                                                                                                                              |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| recordCount          | 検索語に対してヒットした件数。                                                                                                            |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| pageCount            | 検索語に対してヒットした件数のページ数。                                                                                                  |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| result               | 検索結果の親要素。                                                                                                                        |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| site                 | サイト名。                                                                                                                                |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| contentDescription   | コンテンツの説明。                                                                                                                        |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| host                 | ホスト名。                                                                                                                                |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| lastModified         | 最終更新日時。1970/01/01 00:00:00 から始まるミリ秒。                                                                                      |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| cache                | コンテンツの内容。                                                                                                                        |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| score                | ドキュメントのスコア値。                                                                                                                  |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| digest               | ドキュメントのダイジェスト文字列。                                                                                                        |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| tstamp               | ドキュメントの生成日時。1970/01/01 00:00:00 から始まるミリ秒。                                                                            |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| url                  | ドキュメントのURL。                                                                                                                       |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| id                   | ドキュメントのID。                                                                                                                        |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| mimetype             | MIMEタイプ。                                                                                                                              |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| title                | ドキュメントのタイトル。                                                                                                                  |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| contentTitle         | 表示用のドキュメントのタイトル。                                                                                                          |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| contentLength        | ドキュメントのサイズ。                                                                                                                    |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| urlLink              | 検索結果としてのURL。                                                                                                                     |
+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+

Table: レスポンス情報


