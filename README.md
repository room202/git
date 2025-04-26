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

## `Pull`した時に出るエラー対策 その１

### エラー内容

```
Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.
remote: Please see https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/ for more information.
```

### 対策方法

SourceTree のメニューバーから`ツール`→`オプション`→`Git`タブ

`Gitバージョン`の`System`がグレーアウト(選ばれている状態)であることを確認する  
これが`Embedded`がグレーアウト(選ばれている状態)になっていると Push 時に上記エラーが発生するときがある

![](images/100.png)

### 原因の仮説

Git をインストールするよりも前に、SourceTree をインストールすると、この設定になってしまう可能性があります。  
Git をインストールしてから、SourceTree をインストールすれば、問題は発生しないのではないかと考えます。
