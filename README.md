# sentiment-analyis

身近なLINEのトーク履歴を用いてポジネガ分析とワードクラウドを実装してみた。


# Features

日本語の形態素解析にMeCabのipadic-NEologdを用い、新語・固有表現に対応。
またワードクラウドでは任意の形のクラウドを作成できるようにしている。

# Requirement

* mecab-pythin3 1.0.3
* oseti 0.2
* wordcloud 1.8.1

# Installation

## MeCab・oseti・wordcloudのインストールが必要

### MeCabのインストール
```
brew install mecab
brew install mecab-ipadic
#使用したいディレクトリに移動
cd ~/workspace 
#--depth1で最新のコミットのみを取得（大容量のレポジトリをcloneする場合に有効）
git clone --depth 1 https://github.com/neologd/mecab-ipadic-neologd.git
cd mecab-ipadic-neologd
bin/install-mecab-ipadic-neologd -n -a
#途中で"Do you want to install mecab-ipadic-NEoligd?"と聞かれるのでyesとうつ
brew install swig
#pythonでmecabを使えるようにする
pip install mecab-python3
```
ノートブック上で
```
import MeCab
mecab = MeCab.Tagger ('-d /usr/local/lib/mecab/dic/mecab-ipadic-neologd')
```
がエラーなく動けば無事インストール完了

### osetiのインストール
```
brew install oseti
```

### WordCloudのインストール
```
conda install -c conda-forge wordcloud
```

# Usage

jpynbファイルを開いて実行。

# Files

### img_data
実行結果の図が保存されるファイル

### line_data
解析したいLINEのトーク履歴を保存するファイル

### mask_data
ワードクラウドで任意の形のクラウドを作成したい際に、その形の図を保存するファイル

### tempo_data
.jpynbファイルを実行中に一時的に作成されるファイルを格納するファイル

# Note
ワードクラウドの日本語指定パス`fpath`をしっかりと通さないと、作成されるワードクラウドが文字化けしてしまう。
文字化けする場合は、[こちらのサイト](https://zenn.dev/yagiyuki/articles/e05bc37d6c3bc283c5f1)を参考に日本語指定パスを通して対応する。

# Author
* 友利優希（Yuki Tomori）
* 東京大学工学部PSI
* tohoshinki1998@g.ecc.u-tokyo.ac.jp
