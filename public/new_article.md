---
title: shaka-packagerを使って、パッケージング&配信まで
tags:
  - DRM
  - ShakaPackager
private: true
updated_at: '2024-12-11T14:08:17+09:00'
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
$ brew install cmake
```
$ shaka-packagerをクローンする
```
$ git clone https://github.com/google/shaka-packager.git
```
ビルド用のフォルダを準備します
```
$ cd /path/to/shaka-packager
$ mkdir build
$ cd build
```
cmakeビルドとmakeビルドします
```
$ cmake ..
$ make
```
ビルドしたpackagerのバージョンを確認します
```
$ cd path/to/shaka-packager/build/packager
$ ./packager --version
```
これで導入は完了です。

## HLSのWidevineパッケージ化
今回は無料のライセンスサーバーとして、ライセンスサーバー,key,ivを使います。
|:---------------------|:-------------------------------------------------------------------------|
|ライセンスサーバURL      | https://license.uat.widevine.com/cenc/getcontentkey/widevine_test        | 
|Key                  | 1ae8ccd0e7985cc0b6203a55855a1034afc252980e970ca90e5202689f947ab9          | 
|Iv                   | d58ce954203b7c9a9a9d467f59839249                                         | 



```
$ ./packager \
  in=sample.mp4,stream=audio,output=audio.mp4 \
  in=sample.mp4,stream=video,output=video.mp4 \
  --enable_widevine_encryption \
  --key_server_url https://license.uat.widevine.com/cenc/getcontentkey/widevine_test \
  --content_id 7465737420636f6e74656e74206964 \
  --signer widevine_test \
  --aes_signing_key 1ae8ccd0e7985cc0b6203a55855a1034afc252980e970ca90e5202689f947ab9 \
  --aes_signing_iv d58ce954203b7c9a9a9d467f59839249 \
  --hls_master_playlist_output master.m3u8
```
実行すると以下のファイルが生成されます。


### セクション1
セクション1の内容。

### セクション2
セクション2の内容。

## 終わりに
締めの言葉を記述します。
