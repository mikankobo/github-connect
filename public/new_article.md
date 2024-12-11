---
title: shaka-packagerを使って、パッケージング&配信まで
tags:
  - DRM
  - ShakaPackager
private: true
updated_at: '2024-12-10T14:31:49+09:00'
id: ec014bfd05483e5d5a2d
organization_url_name: null
slide: false
ignorePublish: false
---

# 記事のタイトル

## shaka-packagerとは？
Googleが公開している、HLSのパッケージャです。
https://github.com/google/shaka-packager
mp4ファイルをHLSで配信できる形にフォーマットするパッケージになります。

## shaka-packager導入
cmakeをhomebrewでインストールする

```
brew install cmake
```
shaka-packagerをクローンする
```
git clone https://github.com/google/shaka-packager.git
```
ビルド用のフォルダを準備します
```
cd /path/to/shaka-packager
mkdir build
cd build
```
cmakeビルドとmakeビルドします
```
cmake ..
make
```
ビルドしたpackagerのバージョンを確認します
```
cd path/to/shaka-packager/build/packager
./packager --version
```
これで導入は完了です。



### セクション1
セクション1の内容。

### セクション2
セクション2の内容。

## 終わりに
締めの言葉を記述します。
