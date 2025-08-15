# Git

## インストールの手順

### ダウンロード

下記サイトから Git をダウンロードする  
https://git-scm.com/

![](images/001.png)

`64-bit Git for Windows Setup.`をダウンロードする
![](images/002.png)

`ダウンロード`フォルダに保存する  
![](images/003.png)

### インストール

ダウンロードしたファイルを実行  
![](images/004.png)

`Next`をクリック  
![](images/005.png)

`Next`をクリック  
![](images/006.png)

`Windows Explorer integration`のチェックを外して `Next`をクリック  
※`Open Git Bash here`と`Open Git GUI here`のチェックも外れる  
![](images/008.png)

`Next`をクリック  
![](images/009.png)

`Use Visual Studio Code as Git's default editor`に変更して`Next`をクリック  
![](images/011.png)

`Override the default branch name for new repositories`にチェックして`Next`をクリック  
![](images/013.png)

`Next`をクリック  
![](images/014.png)

`Next`をクリック  
![](images/016.png)

`Next`をクリック  
![](images/017.png)

`Next`をクリック  
![](images/018.png)

`Next`をクリック  
![](images/019.png)

`Next`をクリック  
![](images/020.png)

`Next`をクリック  
![](images/021.png)

`Enable symbolic links`にもチェックして`Next`をクリック  
![](images/023.png)

`Next`をクリック  
![](images/024.png)

インストールが始まるので待つ  
![](images/025.png)

`View Release Notes`のチェックを外して `Finish`をクリック  
![](images/027.png)

## インストールの確認

コマンドプロンプトを起動して、下記コマンドを実行

```bash
git --version
```

![](images/028.png)

バージョンが表示されたらインストール成功  
![](images/029.png)


## GitHubとの連携

### PAT方式(Personal Access Tokens)

#### 事前準備

- [アクセストークンの準備](https://github.com/settings/tokens)  
※ Personal access tokens (classic) を使用する

- GitHub上にリモートリポジトリを作成
    - 例) git-practice


#### PC内にあるソースコードをGitHub上で管理したい場合

```bash
cd GitHub管理したいフォルダに移動

# Gitの初期化とファイルを管理に追加
git init
git add -A
git commit -m "First Commit"

# ブランチ名の確認
git status

# ブランチ名が「main」では無い場合、「main」に変更
git branch -m main

# リモートブランチとの紐づけ
git remote add origin https://<ユーザー名>:<アクセストークン>@github.com/xxx/xxx.git
git remote add origin https://room202:ghp_xxx@github.com/room202/git-practice.git

# リモートブランチにプッシュ
git push -u origin main
```

#### GitHub上にあるソースコードをダウンロードしたい場合

```bash
cd GitHub管理したいフォルダに移動

# クローン
git clone https://<ユーザー名>:<アクセストークン>@github.com/xxx/xxx.git
git clone https://room202:ghp_xxx@github.com/room202/git-practice.git
```

### 公開鍵方式

`Git Bash`で実行すること

#### 1. SSH Key(鍵)を生成する

```bash
ssh-keygen -t ed25519 -C "メアド"
```

#### 2. SSH Key(鍵)の保存先を確認

確認できたら`Enter`

```bash
Generating public/private ed25519 key pair.
Enter file in which to save the key (/c/Users/%USERNAME%/.ssh/id_ed25519):
```

#### 3. パスフレーズ(パスワード)を入力する

確認のため２回入力する

```bash
Enter passphrase for "/c/Users/%USERNAME%/.ssh/id_ed25519" (empty for no passphrase):
Enter same passphrase again:
```

#### 4. SSH Key(鍵)をGitHubに登録

SSH Key(公開鍵)をクリップボードにコピーする

```bash
# Windows
clip < /c/Users/%USERNAME%/.ssh/id_ed25519.pub

# macOS
pbcopy < /Users/%USERNAME%/.ssh/id_ed25519.pub
```

#### 5. GitHubの設定画面を表示する

`Settings` → `SSH and GPG Keys` → [New SSH key](https://github.com/settings/keys)

#### 6. 公開鍵を貼り付ける

- Title : わかりやすいタイトル (ex. My Key)
- Key type : Authentication Key
- Key : 公開鍵をペースト

上記を記入して`Add SSH key`をクリック

#### 7. 確認用のコマンドを入力して確認

```bash
ssh -T git@github.com
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes  # ←「yes」と入力する
```

#### 8. パスフレーズ(パスワード)を入力する

```bash
Enter passphrase for key '/c/Users/%USERNAME%/.ssh/id_ed25519': # ← パスフレーズ(パスワード)を入力する

# 下記が表示されたら成功
# 失敗したら`Permission denied`と表示される
You've successfully authenticated, 
```

## コマンドテクニック

ファイルを開く

```bash
# Windows
start ファイル名

# macOS
open ファイル名
```

## `Pull`した時に出るエラー対策 その１

### エラー内容

```
Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.
remote: Please see https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/ for more information.
```

### 対策方法

SourceTree のメニューバーから`ツール`→`オプション`→`Git`タブ

`Gitバージョン`の`System`がグレーアウト(選ばれている状態)であることを確認する  
これが`Embedded`がグレーアウト(選ばれている状態)になっていると Pull 時に上記エラーが発生する可能性があります。

![](images/100.png)

### 原因の仮説

Git をインストールするよりも前に、SourceTree をインストールすると、この設定になってしまう可能性があります。  
Git をインストールしてから、SourceTree をインストールすれば、問題は発生しないのではないかと考えます。
