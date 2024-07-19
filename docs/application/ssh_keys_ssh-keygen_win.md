---
id: ssh_keys_ssh-keygen_win
title: SSH公開鍵・秘密鍵の生成方法 (Windowsの場合)
---

このページでは、Windowsのための、SSH公開鍵の生成方法について詳しい手順を説明しています。

Windowsに標準搭載されているPowerShellを例に、ご説明します。


## PowerShellを起動する {#open-powershell}

![](/img/ssh_keys/windows/ssh_win_intro_1-1.png)


Windowsマークをクリックします。

![](/img/ssh_keys/windows/ssh_win_3.png)

検索ボックスが表示されますので、「&#x1F50D; 検索するには、ここに入力します」をクリックします。クリックする場所は、検索ボックスの中であればどこでも構いません。

![](/img/ssh_keys/windows/ssh_win_4.png)

クリックすると、以下の画像のように表示されます。

![](/img/ssh_keys/windows/ssh_win_5.png)

「PowerShell」もしくは「pwsh」と入力します。

PowerShellは、最新バージョンをインストールすることが推奨されています。最新バージョンのPowerShell は、実行ファイル名がpwsh.exeという名前でインストールされているため、PowerShellを検索するときは、”powershell”ではなく”pwsh”と入力して検索します。

「PowerShell」と「pwsh」の違いについての詳細は、[<u>FAQの「PowerShell 5.1と7.2.6の主な違いはありますか。」をご参照ください</u>](/faq/faq_sshkeys_windows#powershell-51と726の主な違いはありますか)。

![](/img/ssh_keys/windows/ssh_win_6.png)

「PowerShell」と入力した場合は、以下の画面のように検索結果に実行ファイルが表示されます。

![](/img/ssh_keys/windows/ssh_win_7_powershell.png)

「pwsh」と入力した場合は、以下の画面のように検索結果に実行ファイルが表示されます。

![](/img/ssh_keys/windows/ssh_win_7_pwsh.png)

「pwsh」と入力した場合に、もし以下の画面のように、検索結果に実行ファイルが表示されない場合は、まだ最新バージョンのPowerShellがインストールされていない状態ですので、インストールを推奨します。[<u>FAQの「最新バージョンのPowerShellをインストールする方法」を参照して、最新バージョンのPowerShellをインストールしてください</u>](/faq/faq_sshkeys_windows#最新バージョンのpowershellをインストールする方法)。インストールすると、上図の画面のように、検索結果に実行ファイルが表示されるようになります。

![](/img/ssh_keys/windows/ssh_win_7_nonpwsh.png)

「PowerShell」もしくは「pwsh」を入力後、検索結果に実行ファイルが表示されたら、「管理者として実行」をクリックします。

![](/img/ssh_keys/windows/ssh_win_8.png)

「はい」をクリックします。

![](/img/ssh_keys/windows/ssh_win_9.png)

クリックすると、PowerShellが起動します。

![](/img/ssh_keys/windows/ssh_win_10.png)

このとき、「pwsh」と入力したユーザのPowerShellの画面は、以下のように表示されます。上図の表示画面は、2022年10月19日時点での最新バージョン PowerShell 7.2.6を起動したときのPowerShellの画面です。

![](/img/ssh_keys/windows/ssh_win_11.png)

もしこの時に、画面に以下のようなメッセージが表示される場合は、「さらに最新バージョンが発表されているのでアップグレードしてください。」と言われています。[ここをクリックして、FAQの「最新バージョンのPowerShellをインストールする方法」のページに移動して、最新バージョンのPowerShellをインストールしてください](/faq/faq_sshkeys_windows#最新バージョンのpowershellをインストールする方法)。最新バージョンをインストールすると、上図のように、メッセージが表示されなくなります。

```
 A new PowerShell stable release is available: v7.2.7
   Upgrade now, or check out the release page at:
     https://aka.ms/PowerShell-Release?tag=v7.2.7
```

一方、「PowerShell」と入力したユーザのPowerShellの画面は、以下のように表示されます。この表示画面のように、PowerShellのバージョンが古くなっていることを示すメッセージが表示される場合があります。その場合は、本ページの作業に入る前に、PowerShellのバージョンアップを行うことを推奨します。方法については、[<u>FAQの「最新バージョンのPowerShellをインストールする方法」</u>](/faq/faq_sshkeys_windows#最新バージョンのpowershellをインストールする方法)をご参照ください。

![](/img/ssh_keys/windows/ssh_win_PS5_1.png)


PowerShellの画面が表示されると、コマンドプロンプトが表示されます。コマンドプロンプトの最後には「>」が表示されています。コマンドプロンプトが表示されると、コマンドを入力できる状態になります。コマンドプロンプトの後ろで点滅している四角い箱「_」は、カーソルといい、ここにコマンドを入力していきます。

- コマンドを入力するときは、「>」は入力しないでください。「>」はPowerShell 7.2.6が自動で表示するので、ユーザが入力する必要はありません。
- マウスで「>」やカーソルや黒い画面の中をクリックする必要はありません。クリックしても操作できません。カーソルが表示されたら、そのままの状態でコマンドを入力し、[Enter]キーを押します。マウスは使いません。

![](/img/ssh_keys/windows/ssh_win_12.png)


コマンドプロンプトとカーソルが表示されたことを確認したら、SSH公開鍵と秘密鍵を作る前に、OpenSSHクライアントソフトウェアがインストールされているか確認します。

このソフトウェアは、SSH公開鍵と秘密鍵を作ったり、遺伝研スパコンにSSHを用いて通信するためのコマンドを実行するときに使われるソフトウェアです。

インストールされていないと、これ以降の作業ができないので、ここで確認しておきましょう。

以下のコマンドを入力し、[Enter]キーを押します。

```
Get-WindowsCapability -Online | Where-Object Name -like 'OpenSSH*'
```

![](/img/ssh_keys/windows/ssh_win_13.png)

すると、以下のように、OpensSSHクライアントがインストールされている状態かどうかが表示されます。

![](/img/ssh_keys/windows/ssh_win_14.png)

```
Name  : OpenSSH.Client~~~~0.0.1.0
State : Installed
```

このように、「OpenSSH.Client~~~~0.0.1.0」の「State」が "Installed" になっていたら、OpensSSHクライアントがインストールされている状態です。[次の「SSH公開鍵と秘密鍵を作る」に進みます](/application/ssh_keys_windows#ssh公開鍵と秘密鍵を作る-1)。

もし「State」が "NotPresent" になっている場合は、まだOpenSSHクライアントソフトウェアがインストールされていない状態です。[「参考文献」を参照してインストール](/application/ssh_keys_windows#参考文献)してから、次の「SSH公開鍵と秘密鍵を作る」に進んでください。


## SSH公開鍵と秘密鍵を生成する {#generate-ssh-pub-sec-key}

![](/img/ssh_keys/windows/ssh_win_intro_1-2.png)

OpensSSHクライアントのインストールの状態が表示された行の次の行に、新たにコマンドプロンプトとカーソルが表示され、再び、コマンドを入力できる状態になります。

![](/img/ssh_keys/windows/ssh_win_15.png)

以下のコマンドを入力して、[Enter]キーを押します。

```
ssh-keygen -t rsa -b 3072
``` 

![](/img/ssh_keys/windows/ssh_win_16.png)

すると、以下の画面のように、2行表示されます。

![](/img/ssh_keys/windows/ssh_win_17.png)

`Enter file in which to save the key (/Users/your_username/.ssh/id_rsa):`と聞かれます。これは、「作ったSSH公開鍵と秘密鍵をあなたのPCの中のどこに保存しますか。」という意味です。

通常は何も入力しないで、そのまま[Enter]キーを押します。

![](/img/ssh_keys/windows/ssh_win_18.png)

すると、以下の画面のように、２行表示されます。

![](/img/ssh_keys/windows/ssh_win_19.png)

`Enter passphrase (empty for no passphrase):`というメッセージが表示されます。ここにパスフレーズを入力してください。

パスフレーズは遺伝研スパコンのパスワードとは違うものです。長い文字列を自由に設定することが出来ます。
パスフレーズは、ランダムに本を開いた際のページの一行目など、スペースを含む長いランダムな文字列を設定することが想定されています。

<table>
	<tbody>
		<tr>
			<td>SSH では秘密鍵ファイルを所有していることが本人であることの根拠として扱われます。 秘密鍵ファイルを盗まれてしまうとなりすましが可能となります。 パスフレーズの設定は省略することが可能ですが、秘密鍵の盗難時の被害を軽減するために設定することを強く推奨します。</td>
		</tr>
	</tbody>
</table>


パスフレーズを入力して、[Enter]キーを押します。

&#x2757; パスフレーズを入力しても、画面は以下の状態のまま何も変化しません。入力している最中も、以下の画面のまま何も変化しませんが、気にせずそのまま入力していきます。入力が終わったら、[Enter]キーを押します。

![](/img/ssh_keys/windows/ssh_win_20.png)

すると、以下の画面のように表示されます。

![](/img/ssh_keys/windows/ssh_win_21.png)

`Enter same passphrase again: `というメッセージが表示されます。上記で入力したパスフレーズと同じパスフレーズを入力して、[Enter]キーを押します。

&#x2757; パスフレーズを入力しても、画面は以下の状態のまま何も変化しません。入力している最中も、以下の画面のまま何も変化しませんが、気にせずそのまま入力していきます。入力が終わったら、[Enter]キーを押します。

![](/img/ssh_keys/windows/ssh_win_22.png)

すると、以下の画面のように表示されます。

![](/img/ssh_keys/windows/ssh_win_23.png)


### &#x2666;**作ったSSH公開鍵と秘密鍵の存在を確認する** {#check-pub-sec-key}

C:\Users\your_username/.sshというフォルダの中に、SSH公開鍵と秘密鍵が本当に作られているかどうか確認していきます。

![](/img/ssh_keys/windows/ssh_win_24.png)

まず、.sshというフォルダが本当にできているかを確認するために、以下のコマンドを入力して、[Enter]キーを押します。

```
Get-ChildItem -Directory C:\Users\your_username
```

![](/img/ssh_keys/windows/ssh_win_25.png)

すると、以下の画面のように表示され、C:\Users\your_usernameのフォルダの中に、.sshという名前のフォルダが存在していることが確認できます。

![](/img/ssh_keys/windows/ssh_win_26.png)

次に、.sshというフォルダの中に移動して、SSH公開鍵と秘密鍵が本当に作られているかどうか確認していきます。

.sshの中に移動するために、以下のコマンドを入力して、[Enter]キーを押します。

```
Set-Location C:\Users\your_username\.ssh
```

続けて、SSH公開鍵と秘密鍵が本当に作られているかどうか確認するために、以下のコマンドを入力して、[Enter]キーを押します。

```
Get-ChildItem
```

![](/img/ssh_keys/windows/ssh_win_27.png)

すると、以下の画面のように表示され、SSH公開鍵と秘密鍵が本当に作られていることが確認できます。

![](/img/ssh_keys/windows/ssh_win_28.png)


### &#x2666;**作ったSSH公開鍵の中身を確認する** {#check-pub-key}

以下のコマンドを打ち込んで、[Enter]キーを押して、作ったSSH公開鍵の中身を確認します。

```
cat .\id_rsa.pub
```

![](/img/ssh_keys/windows/ssh_win_29.png)

すると、以下の画面のように、作ったSSH公開鍵の中身が表示されます。文字列で書かれているのがわかります。

![](/img/ssh_keys/windows/ssh_win_30.png)

