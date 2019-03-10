2019/01/16に実装されたneo-python [v0.8.3](https://github.com/CityOfZion/neo-python/releases/tag/v0.8.3)
へのアップデートによって、プロンプトを起動した後のコマンドが大きく変更されました。

```ex) create wallet → wallet create```

この問題に対する対処として、変更後のコマンドの一覧とコマンドの内容をここに記しますので、ご参考ください。

コマンドの詳細(英語)はhelpコマンドで閲覧可能です。

なお、以下の表の{}は必ず指定しなければならない引数、()は必要によって付加するオプションとなっています。


コマンドの階層ごとにタブで整形しており、使用するときはスペース区切りでつなげて使用します。
たとえば、ウォレットにトークンを追加する場合
```wallet import token {contract_hash}```となります。

```
config                内部設定
  maxpeers {num}      - 最大peer数の設定
  nep8 {on/off}       - NEP-8機能に関する説明の出力切り替え
  node-requests {block-size} {queue-size}
                      - ブロック/キューのサイズ設定
  output {num}        - logの出力レベルの設定
  sc-debug-notify {on/off} 
                      - 実行中の不具合に対する通知の切り替え
  sc-events {on/off}  - スマートコントラクトの通知切り替え
  vm-log {on/off}     - NEOバーチャルマシンのログ出力
    
sc                    スマートコントラクト開発に関する操作
  build {path}        - Pythonスクリプト(.py)をスマートコントラクトファイル(.avm)にコンパイル
  build_run {path} {storage} {dynamic_invoke} {payable} {params} {returntype}
            (inputs) (--no-parse-addr) (--from-addr) (--owners) (--tx-attr)
                      - Pythonスクリプトをスマートコントラクトファイルにコンパイルしてテスト実行
  debugstorage {on/off}
                      - デバッグ用にデータベースを分けるuse a separate database for smart contract storage item debugging
  deploy {path} {storage} {dynamic_invoke} {payable} {params} (returntype) (--fee)
                      - ブロックチェーン上に、スマートコントラクト(.avm)をデプロイ
  invoke {contract} (inputs) (--attach-neo) (--attach-gas) (--no-parse-addr) (--from-addr) (--fee) (--owners) (--tx-attr)
                      - スマートコントラクト上の関数の呼び出し
  load_run {path} {storage} {dynamic_invoke} {payable} {params} {returntype} (inputs) (--no-parse-addr) (--from-addr)
                      - スマートコントラクトファイル(.avm)を指定して実行

search                アセットやコントラクトの検索
  asset {query}       - 名前、発行者、管理者などでアセットの検索
  contract {query}    - 名前、作成者、内容、メールアドレスからコントラクトの検索

show                  ノードやブロックチェーン情報の表示
  account {address}   - 指定アカウントの所持するアセット群(NEO/GAS)の表示
  asset {asset name, assetId, or "all"}
                      - 指定したアセットの情報またはアセットの一覧を表示
  block {block index or script hash} (tx)
                      - 指定したブロックの情報を表示
  contract {script hash, or "all"} 
                      - 指定したスマートコントラクトの情報を表示
  header {header index or script hash}
                      - 指定したブロックのヘッダ情報を表示 
  mem                 - 使用しているメモリー量とバッファの数を表示
  nodes               - 接続されているpeerを表示
  notifications {block index, an address, or contract script hash}
                      - 指定したコントラクトの実行通知を表示
  state               - ノードの状態を表示
  tx {hash}           - 指定したトランザクションの情報を表示

wallet                - ウォレットに関する操作(コマンド単体では開いているウォレットの情報を表示)
  address             - アドレスに関連する命令
    alias {address} {alias}
                      - アドレスのエイリアスを作成
    create {path}     - ウォレットにアドレスを追加
    delete {address}  - ウォレットからアドレスを削除
    split {address} {asset} {unspent_index} {divisions} (fee)
                      - 指定した個数にアセットを分割
  claim (--from-addr) (--to-addr)
                      - GASの請求
  close               - 開いているウォレットを閉じる
  create {path}       - 新規にウォレットを作成
  export              - ウォレットのエクスポートexport wallet items
    nep2 {address}    - パスフレーズ付きNEP-2形式でウォレットをエクスポート
    wif {address}     - WIF形式でウォレットのエクスポート
  import              - ウォレットのインポートに関するコマンド
    contract_addr {contract_hash} {pubkey}
                      - コントラクトハッシュからインポート
    multisig_addr {own pub key} {sign_cnt} {signing key n}
                      - マルチシグネチャアドレスからインポート
    nep2 {private key}
                      - パスフレーズで保護されたNEP-2形式のプライベートキーからインポート
    token {contract_hash}
                      - トークンのインポート
    watch_addr {address}
                      - 読み取り専用でパブリックアドレスからインポート
    wif {key}         - WIF形式で記録されたプライベートキーからインポート
  open {path}         - ウォレットファイルからウォレットを開く
  rebuild (start_block)
                      - ウォレットのリビルド
  send {asset} {address} {amount} (--from-addr) (--fee) (--owners) (--tx-attr)
                      - アセットを送信する (NEO/GAS)
  sendmany {tx_count} (--change-addr) (--from-addr) (--fee) (--owners) (--tx-attr) 
                      - 複数のトランザクションを送信
  sign {json}         - マルチシグトランザクションに署名
  token               - トークンに関する様々な操作
    allowance {symbol} {from_addr} {to_addr}      
                      - fromアドレスからtoアドレスへのトークン引き出し限度額を取得
    approve {symbol} {from_addr} {to_addr} {amount} (--fee)
                      - fromアドレスからtoアドレスへのトークン引き出し限度額を設定
    delete {contract} - ウォレットからトークンを取り除く
    history {symbol or script hash}
                      - トランザクションの履歴を表示
    mint {symbol} {to_addr} (--attach-neo) (--attach-gas) (--fee) (--tx-attr)
                      - トークンの造幣
    register {symbol} {addresses} (--fee)
                      - クラウドセールに登録
    send  {token} {from_addr} {to_addr} {amount} (--fee) (--tx-attr)
                      - ウォレットからトークンを送信
    sendfrom {token} {from_addr} {to_addr} {amount} (--fee)
                      - 別のアカウントに代わりトークンを送信(要認証) (requires approval)
  unspent (asset) (--from-addr) (--watch) (--count)
                      - show unspent assets
  verbose             - 詳細なウォレットの情報を表示

help                  コマンドの解説を表示
quit                  プロンプトを終了する
```
