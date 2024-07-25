---
id: Archaea_tools
title: Archaea tools(旧 HCPtools) の使い方
---


遺伝研スパコンに対してファイルのアップロード、ダウンロードを行うには、一般的に広く用いられているファイル転送ソフトウェアである`scp`や`sftp`をつかうことができますが、`scp`などでは遠距離間で大量のファイルを転送する際に転送速度が遅くなる性質があります。

遠距離の高速通信のために、遺伝研スパコンでは、一般解析区画では Aspera、個人ゲノム解析区画では Archaea tools(旧 HCPtools)というファイル転送ソフトウェアが利用可能となっています。



参考資料

- 各製品ごとの公式マニュアルは、[&#x1f517;<u>Bytix 公式ページ「ドキュメント」のページをご参照ください</u>](https://support.bytix.tech/document/)。
- 最新バージョンは、[&#x1f517;<u>Bytix 公式ページ「ダウンロード【最新版】」のページをご参照ください</u>](https://support.bytix.tech/latest/)。
- [<u>FAQ（よくある質問）: HCP tools</u>](/faq/faq_hcptools)


## ソフトウェアの改称について {#renaming-of-software}

2022 年 10 月、HCPtools ソフトウェア提供元が、データ転送系のブランド名称として、「Bytix(バイティックス)」というブランド名を立ち上げ、製品名称が「HCPtools」から「Archaea tools」へ変更になりました。

製品名称変更後も、これまで通り HCPtools で使用していたコマンドと同じコマンドをそのままお使いいただけます。

変更についての詳細は、[&#x1f517;<u>Bytix 公式ページ「製品名称変更等について」のページをご参照ください</u>](https://support.bytix.tech/important/)。




## クライアントソフトウェアのインストール {#install-client-software}

Archaea tools(旧 HCPtools)を利用するためにはクライアントソフトウェアをユーザのクライアント計算機にインストールする必要があります。
お使いのクライアント計算機の環境に応じて以下の文書をご参照ください。

- Linux の場合 (Windows の WSL2 環境の場合も含む）
    - [&#x1f517;<u>Ubuntu Linux</u>](https://support.bytix.tech/docs/archaea/tools/1.4/B_setup_client/B04_Ubuntu)
    - [&#x1f517;<u>CentOS 7</u>](https://support.bytix.tech/docs/archaea/tools/1.4/B_setup_client/B03_RHEL)
- [&#x1f517;<u>Mac OS の場合</u>](https://support.bytix.tech/docs/archaea/tools/1.4/B_setup_client/B02_macOS/)
- [&#x1f517;<u>Windows の場合</u>](https://support.bytix.tech/docs/archaea/tools/1.4/B_setup_client/B01_Windows)


## 設定ファイルの設置方法 {#setup-configfile}

遺伝研スパコンとのデータの受送信を行うためにはホームディレクトリに Archaea tools(旧 HCPtools)の設定ファイルを設置する必要があります。遺伝研スパコン用の設定ファイルは github からクローンして取得してください。

Linux (Windows の WSL2 環境の場合も含む)
```
cd $HOME
git clone https://github.com/nig-sc/Bytix_Archaea/ .hcp
```

Mac OS の場合
```
cd $HOME
git clone https://github.com/nig-sc/Bytix_Archaea/ .hcp
```

Windows (PowerShell)の場合
```
cd $HOME
git clone https://github.com/nig-sc/Bytix_Archaea/ _hcp
```

git clone すると以下のファイルが作られます。

```
$ tree .hcp
.hcp
├── README.md
├── hchmod.conf
├── hchown.conf
├── hcp-common.conf
├── hcp-ls.conf
├── hcp.conf
├── hln.conf
├── hmkdir.conf
├── hmv.conf
├── hpwd.conf
├── hrm.conf
└── hsync.conf

1 directory, 12 files
```


次に秘密鍵の絶対パスを設定ファイル hcp-common.conf の中に以下のように書いてください。


hcp-common.conf の中身
```
PrivateKeyFile /home/youraccount/.ssh/id_rsa    # 秘密鍵の絶対パス
AcceptableCryptMethod   PLAIN                # 暗号化:なし
AcceptableDigestMethod  SHA256               # ダイジェスト方式: SHA256
DisableDataIntegrityChecking yes             # ダイジェスト方式なしを許可
```

Mac OS の場合
```
PrivateKeyFile /Users/youraccount/.ssh/id_rsa    # 秘密鍵の絶対パス
```

Windows (PowerShell)の場合
```
PrivateKeyFile C:\Users\youraccount\.ssh/id_rsa    # 秘密鍵の絶対パス
```



## ファイル転送 {#filetransfer-archaeatools}


### 個人ゲノム解析区画への SSL-VPN 接続 {#filetransfer-archaeatools#sshvpn-pg}

個人ゲノム解析区画とのファイルの転送を行うために、まず最初にクライアント計算機と遺伝研スパコン個人ゲノム解析区画との間で SSL-VPN 接続を行う必要があります。


接続方法は、[<u>「ログイン方法(個人ゲノム解析区画)」の「VPN への接続方法」</u>](/personal_genome_division/pg_login#vpn%E3%81%B8%E3%81%AE%E6%8E%A5%E7%B6%9A%E6%96%B9%E6%B3%95)をご参照ください。

![](upload_download.png)


### アップロード {#filetransfer-archaeatools#upload}

ユーザのクライアント計算機でターミナルエミュレータを起動し以下のコマンドを実行します。

Linux (Windows の WSL2 環境の場合も含む）の場合
```
hcp --user youraccountname --hpfp \
   /home/youraccountname/your_file.txt \
   gwa.ddbj.nig.ac.jp:/home/your_account-pg/some_directory/your_file.txt
```

Mac OS の場合
```
hcp --user youraccountname --hpfp \
   /Users/youraccountname/your_file.txt \
   gwa.ddbj.nig.ac.jp:/home/your_account-pg/some_directory/your_file.txt
```

Windows (PowerShell)の場合
```
hcp --user youraccountname --hpfp \
    C:\Users\youraccountname\your_file.txt \
    gwa.ddbj.nig.ac.jp:/home/your_account-pg/some_directory/your_file.txt
```

### ダウンロード {#filetransfer-archaeatools#download}


ユーザのクライアント計算機でターミナルエミュレータを起動し以下のコマンドを実行します。


```
hcp --user youraccountname --hpfp  \
    gwa.ddbj.nig.ac.jp:/home/your_account-pg/some_directory/your_file.txt \
    C:\Users\youraccountname\your_file.txt
```

### 注意 {#filetransfer-archaeatools#note}
初めてデータ転送を行う時に以下のメッセージが表示されます。ここは yes と入力してください。

```
Are you sure you want to continue connecting [yes/no] ?
```


## ファイル転送でよく使うオプション {#filetransfer-archaeatools#options}

オプションの詳細については、[&#x1f517;<u>公式マニュアルのコマンドリファレンス</u>](https://support.bytix.tech/document/)をご参照下さい。


- `--hpfp` : UDP(HpFP2)通信の指定で、遠距離間の通信を高速化します
    - このオプションを省略すると、通常広く用いられている TCP 通信を行います。
- `-p` : 転送元のパーミッションを保持します。
- `-R` : ディレクトリごと再帰的にファイルを転送します。
- `-r` : ファイル転送の再開処理（リジューム）を行う。
    - レジューム機能の詳細については、<a href="https://support.bytix.tech/docs/archaea/tools/1.4/D_commandRef/D01_hcp/#r-resume">&#x1f517;<u>公式マニュアルのコマンドリファレンス内の「通信再開機能   r, resume」</u></a>をご参照ください。
- `-y` : データの完全性（転送途中でエラーや改ざんがないか）の確認を行います。
- `-z` : 転送時にデータの圧縮を行います。


## その他のコマンド {#filetransfer-archaeatools#other-commands}


| コマンド | 機能                                     |
|----------|------------------------------------------|
| `hrm`    | サーバ上のファイルを削除                 |
| `hcp-ls` | サーバ上のファイル一覧を表示             |
| `hmkdir` | サーバ上にディレクトリ作成               |
| `hpwd`   | サーバ上のワーキングディレクトリ表示     |
| `hmv`    | サーバ上のファイルを移動                 |
| `hlm`    | サーバ上にシンボリックリンク等を作成     |
| `hchmod` | サーバ上のファイルのパーミッションを変更 |
| `hchown` | サーバ上のファイルの所有者を変更         |
| `hsync`  | サーバ上のファイルと同期                 |

詳細については、[&#x1f517;<u>公式マニュアル</u>](https://support.bytix.tech/document/)をご参照下さい。




[def]: https://support.bytix.tech/docs/archaea/tools/1.4/D_commandRef/D01_hcp#r-resume
