---

## KrugleAI  Offline Installation Guide

This guide provides instructions for downloading and installing KrugleAI models offline. Follow the steps below to ensure a smooth installation process.

---

### Step 1: LLMモデル・ウェイト・ファイルのダウンロード


利用可能なダウンロード用モデル：
- KrugleAI-Code-15B-Chat-V2.0-GGUF.Q5_K_M
- KrugleAI-Code-35B-Chat-V1.0-GGUF.Q5_K_M (KrugleAI Proをご購入のお客様向け)
- KrugleAI-text-embedding-V1.0-GGUF.Q8_0

---
#### 1-1. モデルをダウンロードするディレクトリを作成し、移動します。

---
#### 1-2. モデルダウンロードに必要なGit LFSをインストールします。Git LFSがインストールされていない場合は、以下のコマンドを実行してGit LFSをインストールします:
```shell
apt-get install -y git-lfs
# Make sure git-lfs is installed (https://git-lfs.com)
git lfs install
```

Windows端末でダウンロードする場合は、Gitをインストールしたのちに、下記コマンドでgit LFSがインストールされていることを確認してください。
```shell
PS C:\Users\ki-krugle-jp> git lfs install
Git LFS initialized.
PS C:\Users\ki-krugle-jp>
```

---
#### 1-3. LLMウェイトファイル（例：KrugleAI-Code-15B-Chat-V2.0-GGUF.Q5_K_M）をダウンロードします。

*Note: username, passwordは、Krugle担当者にお問い合わせください。 

モデルをダウンロードするには以下のコマンドを実行します：

Krugle Code LLM 15B Model(15Bユーザ様用):
```shell
# linux
username=<username>
password=<password>
git clone https://${username}:${password}@huggingface.co/krugle/KrugleAI-Code-15B-Chat-V2.0-GGUF.Q5_K_M \  
          krugle_KrugleAI-Code-15B-Chat-V2.0-GGUF.Q5_K_M
```

Krugle Code LLM 35B Model(35Bユーザ様用):
```shell
# linux
username=<username>
password=<password>
git clone https://${username}:${password}@huggingface.co/krugle/KrugleAI-Code-35B-Chat-V1.0-GGUF.Q5_K_M \  
          krugle_KrugleAI-Code-35B-Chat-V1.0-GGUF.Q5_K_M
```


```pshell
# Windows PowerShellでの実行例

PS C:\Users\ki-krugle-jp\.models>  git clone https://<username>:<password>@huggingface.co/krugle/KrugleAI-Code-35B-Chat-V1.0-GGUF.Q5_K_M krugle_KrugleAI-Code-35B-Chat-V1.0-GGUF.Q5_K_M
Cloning into 'krugle_KrugleAI-Code-35B-Chat-V1.0-GGUF.Q5_K_M'...
remote: Enumerating objects: 149, done.
remote: Total 149 (delta 0), reused 0 (delta 0), pack-reused 149 (from 1)
Receiving objects: 100% (149/149), 53.51 KiB | 2.06 MiB/s, done.
Resolving deltas: 100% (46/46), done.
Filtering content:  17% (8/46), 3.90 GiB | 90.80 MiB/s
```
---
Krugle Code LLM Text Embedding Model(共通):
```shell
git clone https://<username>:<password>@huggingface.co/krugle/KrugleAI-text-embedding-V1.0-GGUF.Q8_0 \
          krugle_KrugleAI-text-embedding-V1.0-GGUF.Q8_0
```



```shell
# 実行例: 
root@demo1-aio:~/.model# git clone https://krugleclient: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@huggingface.co/krugle/KrugleAI-Code-35B-Chat-V1.0-GGUF.Q5_K_M krugle_KrugleAI-Code-35B-Chat-V1.0-GGUF.Q5_K_M
Cloning into 'krugle_KrugleAI-Code-35B-Chat-V1.0-GGUF.Q5_K_M'...
remote: Enumerating objects: 149, done.
remote: Total 149 (delta 0), reused 0 (delta 0), pack-reused 149 (from 1)
Receiving objects: 100% (149/149), 53.51 KiB | 26.75 MiB/s, done.
Resolving deltas: 100% (46/46), done.
Filtering content: 100% (46/46), 22.15 GiB | 102.85 MiB/s, done.
root@demo1-aio:~/.model#
root@demo1-aio:~/.model#
root@demo1-aio:~/.model# ls
krugle_KrugleAI-Code-35B-Chat-V1.0-GGUF.Q5_K_M
root@demo1-aio:~/.model#
root@demo1-aio:~/.model#
```

```shell
# 実行例: 
root@demo1-aio:~/.model# git clone https://krugleclient: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@huggingface.co/krugle/KrugleAI-text-embedding-V1.0-GGUF.Q8_0 \
          krugle_KrugleAI-text-embedding-V1.0-GGUF.Q8_0
Cloning into 'krugle_KrugleAI-text-embedding-V1.0-GGUF.Q8_0'...
remote: Enumerating objects: 15, done.
remote: Counting objects: 100% (10/10), done.
remote: Compressing objects: 100% (9/9), done.
remote: Total 15 (delta 3), reused 0 (delta 0), pack-reused 5 (from 1)
Unpacking objects: 100% (15/15), 5.49 KiB | 936.00 KiB/s, done.
root@demo1-aio:~/.model#
```


---
### Step2. モデルの配置:


#### 2-1. Krugle AiOサーバにログインし、rootユーザに切り替えます。

#### 2-2. /rootディレクトリに.modelsディレクトリを作成します。


```shell
cd /root
mkdir .models
cd .models
```

#### 2-3. Step1でダウンロードしたファイルをディレクトリごと、.modelsディレクトリに移動します。


```shell
root@demo1-aio:~# cd .models/
root@demo1-aio:~/.models# ls -lh
total 8.0K
drwxr-xr-x 3 root root 4.0K Jan 30 15:56 krugle_KrugleAI-Code-35B-Chat-V1.0-GGUF.Q5_K_M
drwxr-xr-x 3 root root 4.0K Jan 30 15:57 krugle_KrugleAI-text-embedding-V1.0-GGUF.Q8_0
root@demo1-aio:~/.models#

```

### Step3. モデルのインストール:

#### 3-1. .modelsディレクトリの親ディレクトリ/rootに移動します。

```shell
cd /root
```

#### 3-2. ls -la /root/.modelsコマンドで.modelsディレクトリにモデル用ディレクトリが存在していることを確認します。

```shell
root@demo1-aio:~# ls -l /root/.models
total 8
drwxr-xr-x 3 root root 4096 Jan 30 16:19 krugle_KrugleAI-Code-35B-Chat-V1.0-GGUF.Q5_K_M
drwxr-xr-x 3 root root 4096 Jan 30 16:19 krugle_KrugleAI-text-embedding-V1.0-GGUF.Q8_0
root@demo1-aio:~#
```

#### 3-3. shasta initの実行

次に、以下のコマンドを実行します：
```shell
# For Linux
shasta init

```

##### 3-3-a. Offlineインストールの選択

「Enter Y for offline installation, or any other key for online installation:」が表示されたら:
```text
`Y`と入力してください。
```

##### 3-3-b . Modelの選択

「Please choose an LLM to install:」と表示されたら、15Bモデルの場合はA、35Bモデルの場合はCを選択します。


```text
Please choose an LLM to install:

A) ✨🥇 [KrugleAI Code 15B + KrugleAI Text Embedding] - SIZE: 10.15 GB RAM/VRAM: 15+ GB
B) [KrugleAI Code 10B + KrugleAI Text Embedding] - SIZE: 8.85 GB RAM/VRAM: 15+ GB
C) [KrugleAI Code 35B + KrugleAI Text Embedding] - SIZE: 23.15 GB RAM/VRAM: 48+ GB

Enter your choice:
```

##### 3-3-c. モデルの初期化完了の確認

「KrugleAI models have been initialized.」が表示されたら、モデルの初期化が完了しています。


```text
root@demo1-aio:~# shasta init

Do you want to perform an offline installation of LLM models?
(Offline installation requires LLM data to be pre-downloaded and extracted to the shasta installation root directory)
Enter Y for offline installation, or any other key for online installation: Y

Offline Installation Mode Selected
Please ensure that the LLM model data has been downloaded and extracted to the shasta installation root directory.
The directory structure should match what would be created during online installation.

Please choose an LLM to install:

A) ✨🥇 [KrugleAI Code 15B + KrugleAI Text Embedding] - SIZE: 10.15 GB RAM/VRAM: 15+ GB
B) [KrugleAI Code 10B + KrugleAI Text Embedding] - SIZE: 8.85 GB RAM/VRAM: 15+ GB
C) [KrugleAI Code 35B + KrugleAI Text Embedding] - SIZE: 23.15 GB RAM/VRAM: 48+ GB

Enter your choice: C
You chose: [KrugleAI Code 35B + KrugleAI Text Embedding] - SIZE: 23.15 GB RAM/VRAM: 48+ GB

Installing KrugleAI models... -Using pre-downloaded model files for KrugleAI-Code-35B-Chat-V1.0-GGUF.Q5_K_M
Installing KrugleAI models... -Loaded model in state 1
Installing KrugleAI models... -Using pre-downloaded model files for KrugleAI-text-embedding-V1.0-GGUF.Q8_0
✅ KrugleAI models have been initialized.
root@demo1-aio:~#

```

##### 3-3-d. モデルの確認

shasta lsコマンドでモデルがインストールされていることを確認します。

```shell
shasta ls

# 出力例:
root@demo1-aio:~# shasta ls
NAME                            ID              SIZE      MODIFIED
krugle-code-35b-chat:latest     1cd24b5d88c7    23 GB     5 minutes ago
krugle-text-embedding:latest    8f915b91a077    146 MB    5 minutes ago
root@demo1-aio:~#
```