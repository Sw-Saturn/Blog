---
title: "Raspberry PiをNAS化した"
date: 2020-05-19T12:20:00+09:00
draft: false
author: "Kanta Demizu"
summary: "便利やね"
tags: ["Raspberry Pi"]
share: true
toc: true
thumbnail: "https://blog.foto.ne.jp/free/images/fd400158_w420.jpg"
slug: naspi
---

## はじめに

こんにちは。RAWファイルのバックアップを取り忘れて困った人です。

今メインで使っているMacのストレージ容量が少なく、USB接続の外付けHDDを使っています。

いちいち繋げるのも面倒で家にラズパイが転がっていたのでNAS化してみました。

## やり方

|必要なもの||
|----------|-|
|Raspberry Pi|x1|
|USB HDD|x1|

今回はOSにRaspbian GNU/Linux 10 (buster)を使用しました。

公開鍵認証とかしたいならSFTPサーバを構築するのもアリですが、家庭内LANでの利用なのでSambaで構築します。

さて、サクッと必要なパッケージをインストールします。
HDDのフォーマットがexFATなのでexfat-fuseとexfat-utilsも導入。

    sudo apt install samba exfat-fuse exfat-utils

起動時に自動でHDDをマウントさせるように設定しましょう。
UUIDを調べます。

    sudo blkid

fstabに記述。マウントポイントは/media/NASに設定します。

    sudo vim /etc/fstab

以下を追記。(調べたUUID)は適宜置き換え。

    UUID=(調べたUUID) /media/NAS exfat defaults 0 0

再起動して、ストレージがマウントされたことを確認できればOKです。

次に、Sambaの設定をしていきましょう。

    sudo vim /etc/samba/smb.conf

今回は以下のように設定。

    [global]
        min protocol = SMB2
        vfs objects = catia fruit streams_xattr
        fruit:aapl = yes
        fruit:metadata = netatalk
        fruit:model = Xserve # Finder用アイコン設定
        fruit:posix_rename = yes
        fruit:veto_appledouble = no
        fruit:wipe_intentionally_left_blank_rfork = yes
        fruit:delete_empty_adfiles = yes
        workgroup = WORKGROUP
        server string = NasPi
        dos charset = CP932 # Windows用に文字コード設定
        log level = 1 # 書き込み回数を減らす

    [NAS]
        comment = Share
        path = /media/NAS
        guest ok = no
        public = yes
        read only = no
        browsable = yes
        force user = pi

Finder用のアイコンも設定できるっぽくて良いですね。複数台あっても区別つきそう。

*fruit:model*の内容は/System/Library/CoreServices/CoreTypes.bundle/Contents/Info.plistに記載されているモデル名を利用できるようです。([参考](https://wiki.samba.org/index.php/Configure_Samba_to_Work_Better_with_Mac_OS_X))

設定を終えたら、smbdを再起動しましょう。

    sudo systemctl restart smbd.service

LANに接続すると、FinderのサイドバーにNASが表示されるはずです。

もしくはFinderを開き⌘+Kを押して、smb://{{NASのホスト名}}に接続すると繋がるかと思います。

## 使ってみて

音楽とか写真とかを入れて再生してみたのですが、少しもたつきは感じますが便利です。

ノートPCに直接繋ぐケーブルを減らせるのはやっぱり良いですね。
