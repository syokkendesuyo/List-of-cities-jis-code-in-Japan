# List-of-cities-jis-code-in-Japan

このレポジトリは日本の都道府県および市区町村コードをJsonまたはCSVで提供します。

総務省が提供する市区町村コードは計算で使用されていないのにも関わらずExcelで作成されていました。
そのためJsonとCSVで市町村コードを使用できるように整形しました。

---

### データ

Json, CSVどちらも同一のカラム名、同一の内容で取得できます。

#### カラム定義

| カラム名                  | カラム型 | カラム内容                                                   | 備考                                                         |
| ------------------------- | -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| jis_prefecture_code       | string   | 都道府県コード                                               | 一般的に6桁コードと言われる<br />先頭に0が入る可能性があるためstring型 |
| jis_prefecture_code_no_cd | string   | 都道府県コード (チェックデジットなし)                        | 一般的に5桁コードと言われる<br />先頭に0が入る可能性があるためstring<br />都道府県コードから誤り検出用のコード (6桁目) が削除されたデータ |
| prifecture_kanji          | string   | 都道府県名 (漢字)                                            |                                                              |
| city_kanji                | string   | 市区町村名 (漢字)                                            |                                                              |
| prifecture_kana_hankaku   | string   | 都道府県名 (半角カタカナ)                                    |                                                              |
| city_kana_hankaku         | string   | 市区町村名 (半角カタカナ)                                    |                                                              |
| prefecture_kana_zenkaku   | string   | 都道府県名 (全角カタナカ)                                    |                                                              |
| city_kana_zenkaku         | string   | 市区町村名 (全角カタカナ)                                    |                                                              |
| is_designated             | boolean  | 政令指定都市かどうか (true: 政令指定都市, false: 政令指定都市でない) |                                                              |
| is_designated_figure      | int      | 政令指定都市かどうか (0: 政令指定都市, 0: 政令指定都市でない) |                                                              |

#### コード

基本的なコード構成は下記のとおりです。

| 桁    | 説明                                                         | 備考                                                         |
| ----- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1桁目 | 都道府県コード1桁目<br />01から47までの数字の1桁目が[JISX0401](https://www.jisc.go.jp/app/jis/general/GnrJISNumberNameSearchList?show&jisStdNo=X0401)に従い決定 |                                                              |
| 2桁目 | 都道府県コード2桁目<br />01から47までの数字の2桁目が[JISX0401](https://www.jisc.go.jp/app/jis/general/GnrJISNumberNameSearchList?show&jisStdNo=X0401)に従い決定 |                                                              |
| 3桁目 | 市町村コード1桁目<br />[JISX0402](https://www.jisc.go.jp/app/jis/general/GnrJISNumberNameSearchList?show&jisStdNo=X0402)に従い決定 | 0: 都道府県である<br />1: 政令指定都市である<br />2: 市である<br />3～7: 町村である |
| 4桁目 | 市町村コード2桁目<br />[JISX0402](https://www.jisc.go.jp/app/jis/general/GnrJISNumberNameSearchList?show&jisStdNo=X0402)に従い決定 | 詳細な取り決めによって決定される                             |
| 5桁目 | 市町村コード3桁目<br />[JISX0402](https://www.jisc.go.jp/app/jis/general/GnrJISNumberNameSearchList?show&jisStdNo=X0402)に従い決定 | 詳細な取り決めによって決定される                             |
| 6桁目 | チェックデジット                                             | 5桁コードの場合、省略<br />1～5桁目の数字から生成される0～9までの桁 |

※詳細は[全国地方公共団体コード](https://www.soumu.go.jp/denshijiti/code.html)の仕様書をご確認ください。

#### ファイル容量

2020年5月1日のデータの場合、Json (712KB) とCSV (200KB) を比較するとJsonはデータ量が約3.5倍あります。
取り扱う内容に応じて利用する形式をご検討ください。

---

### 出典元

#### 総務省

このレポジトリ作成にあたって使用したデータはこちらで誰でもダウンロードできます。 (Excel, PDF)

[全国地方公共団体コード](https://www.soumu.go.jp/denshijiti/code.html)

#### JIS規格

このレポジトリで提供されるデータは下記の日本産業規格 (JIS) でも取り決めが行われています。

- [JISX0401](https://www.jisc.go.jp/app/jis/general/GnrJISNumberNameSearchList?show&jisStdNo=X0401)
- [JISX0402](https://www.jisc.go.jp/app/jis/general/GnrJISNumberNameSearchList?show&jisStdNo=X0402)

