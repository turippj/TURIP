# TURIPマニフェスト仕様

## 概要

マニフェストはTURIPデバイスの利用方法を知ることのできるJSONフォーマットからなるテキストデータです。
マニフェストはTURIP管理組織のリポジトリ(manifest.turip.org)に保管されます。

## データ構造

マニフェストのエンコードはUTF-8です。
TURIPのManifestを構成する要素を以下に示します。

Key         | Value type | 概要
------------|------------|------------------------------------
protocol    | string     | TURIPのバージョン("TURIP0.20")
model       | string     | TURIPデバイスの型番(TURIP ID 上位32bit, 16進数表記)
name        | string     | TURIPデバイス名
description | string     | TURIPデバイスの説明文
interface   | string[]   | TURIPデバイスが持つインターフェイス
port        | object[]   | ポート構成の定義

### "interface"

"interface"では、TURIPデバイスが持つインターフェイスを列挙します。
以下に種別を示します。

Value    | 内容
---------|------------------------------------------
"spi"    | シリアルペリフェラルインターフェイス(SPI)
"serial" | 調歩同期式シリアルインターフェイス(UART)
"HTTP"   | HTTPサーバ

### "port"オブジェクト

portオブジェクトは、TURIPモジュールにどのようなポートが存在するかを示すものです。
以下に構造を示します。

Key         | Value type | 概要
------------|------------|-----------------------------
number      | integer    | ポート番号
name        | string     | ポート名
description | string     | ポートの説明
type        | string     | TURIPデータ型
permission  | string     | ポートへの読み書き許可


#### "number"

このキーは必須です。
ポート番号を記述します。

#### "name"

このキーは必須です。
ポートの名前です。

#### "description"

このキーはオプション(推奨)です。
ポートの説明を記述します。

#### "type"

このキーは必須です。
TURIPデータ型を記述します。

#### "permission"

このキーはオプションです。ポートの読み書きに制限があるかどうかを示します。
値は以下の通りです。

Value | 説明
------|-------------
"R"  | 読み取り専用
"W"  | 書き込み専用
"RW"  | 読み書き可能（デフォルト）
