---
id: faq_sshkeys_mac
title: "SSH公開鍵登録の詳細(Macの場合)"
---

## &#x1F180; `ssh -V`と入力して実行すると、`-bash: ssh: command not found`と出力されました。 {#ssh-command-not-found}

&#x1F150; OpenSSHクライアントがインストールされていない状態ですので、まず、以下のコマンドを実行して、インストールしてください。

```
sudo apt update
sudo apt upgrade
sudo apt install -y ssh openssh-client
```

次に、以下のコマンドを実行します。
```
ssh -V
```

実行したあとに、以下のようにOpenSSHクライアントソフトウェアのバージョンが表示されれば、インストールが完了している状態です。

![](ssh_mac_11.png)


