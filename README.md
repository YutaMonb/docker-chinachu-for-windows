# docker-chinachu-for-windows
ChinachuをDockerコンテナに閉じ込めて、Docker for Windowsで動作させることを想定させた作りに変更しました。

[こちら](https://github.com/Chinachu/docker-mirakurun-chinachu) からのForkです。
素晴らしいリポジトリを作ってくださった @h-mineta さんに感謝。

## Constitution
### Chinachu
- Alpine Linux 3.6
- [Chinachu](https://github.com/kanreisa/Chinachu)
  - branch: gamma

## 動作確認環境
Docker CC for Windows (17.06.2-ce-win27) にて起動は確認しています。

詳しい動作環境については下記ブログ記事を参照してください。

http://yanoshi.hatenablog.jp/entry/2017/07/10/022843

## 利用方法
`docker-compose.yml` における `extra_hosts` に記載されている値は、各環境に合わせて変更する必要があるでしょう。

Mirakurunが動作するPC(概ねDocker for Windowsが動作するホストPC)のIPアドレスを指定すると幸せになれるはずです。


## 設定
エリア、環境によって変更が必要なファイルは下記の通りとなります

### 録画ファイル保存先
また録画ファイルはプロジェクトフォルダ内の./recordedに保存されます  
> 保存先を別HDDにしたい場合は、docker-compose.ymlの
>> ./recorded:/usr/local/chinachu/recorded
>
> の./recordedを変更することで保存先を変更可能

## License
This software is released under the MIT License, see LICENSE.
