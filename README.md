## Automatic Raid Battle
--- 編集中 / now writing ---

#### What we need
- マイコン本体 ATmega32u4 など [example](https://www.amazon.co.jp/dp/B07GKR9J4N/)
- micro USBケーブル [example](https://www.amazon.co.jp/dp/B0711PVX6Z/)

#### How to use
1. このレポジトリを clone download する
2. [lufa](https://github.com/abcminiuser/lufa/) を lufa フォルダに入れる
3. avr-gcc avr-dude をインストール
4. makefile 設定する
5. make コマンド
6. マイコンに書き込み （dfu-programmer など）
7. ニンテンドースイッチとマイコンを繋げる
8. Done

#### Reference
- [NintendoSwitchをPCから操作する](https://blog.feelmy.net/control-nintendo-switch-from-computer/)
- [ゼルダの雪玉ボウル自動化](https://github.com/bertrandom/snowball-thrower)
- [【剣盾】無限ワット自動化スレ >>131](https://medaka.5ch.net/test/read.cgi/poke/1574816324/131)
- [Switch「ゼノブレイド2」でマクロを実行してみよう](http://gamemos.blog.jp/archives/6608328.html)
- [dfu-programmer で Arduino UNO の ATmega16U2 に Windows から書き込む](https://another.maple4ever.net/archives/2380/)
- [Switch版DEAD OR ALIVE Xtreme3 Scarlet (DOAX3S) 自動プレイ](https://randdtips.com/switch-doax3s-autoplay/)

#### Note
##### 事前準備
- 設定
    - 「自動で送る」にしておく
    - 「ニックネームを登録しない」にしておく
    - (インターネットをオフにしておく)
- ボックス
    - 捕まえたポケモンが預けられてもいいボックスにして閉じておく
- ボール
    - 念のため大事なボールはボックスのポケモンに持たせておく
    - **バッグの並び順において、モンスターボールの一つ前のボールが使われるらしい？(要検証)(バッグの一番したのボールが使われると勘違いしていました。ごめんなさい)**
    - そこに不要なボールを置いておく
    - バッグの順番はお気に入り+並び替えで変更できる
- ねがいのかたまり
    - たくさん用意しておく
    - ボックスの空き数などにあわせて個数を調整してもよい
- ポケモン
    - 戦わせたいポケモンを手持ちの先頭に持ってくる
    - 撃ちたい技を一番上に持ってくる

##### 仕組み
- ずっと右スティックの上押しっぱなし
    - 「ポケモンを変える」を押さないようにするため
- 一定間隔で「十字キー左押してすぐAボタン」を繰り返す
    - 十字キー左を押すことでダイマックスできる
    - 最後の報酬画面で十字キー左により「次へ」にカーソルを合わせることができる
    - あまり間隔が短いと「ポケモンを変える」を押してしまいそうなので、長めにしている

#### Compiling and Flashing onto the Teensy 2.0++
Go to the Teensy website and download/install the [Teensy Loader application](https://www.pjrc.com/teensy/loader.html). For Linux, follow their instructions for installing the [GCC Compiler and Tools](https://www.pjrc.com/teensy/gcc.html). For Windows, you will need the [latest AVR toolchain](http://www.atmel.com/tools/atmelavrtoolchainforwindows.aspx) from the Atmel site. See [this issue](https://github.com/LightningStalker/Splatmeme-Printer/issues/10) and [this thread](http://gbatemp.net/threads/how-to-use-shinyquagsires-splatoon-2-post-printer.479497/) on GBAtemp for more information. (Note for Mac users - the AVR MacPack is now called AVR CrossPack. If that does not work, you can try installing `avr-gcc` with `brew`.)

LUFA has been included as a git submodule, so cloning the repo like this:

```
git clone --recursive git@github.com:john-ditto/timewalk-with-watt.git
```

will put LUFA in the right directory.

Now you should be ready to rock. Open a terminal window in the `timewalk-with-watt` directory, type `make`, and hit enter to compile. If all goes well, the printout in the terminal will let you know it finished the build! Follow the directions on flashing `Joystick.hex` onto your Teensy, which can be found page where you downloaded the Teensy Loader application.

#### Thanks

Thanks [snowball-thrower](https://github.com/bertrandom/snowball-thrower)

Thanks to Shiny Quagsire for his [Splatoon post printer](https://github.com/shinyquagsire23/Switch-Fightstick) and progmem for his [original discovery](https://github.com/progmem/Switch-Fightstick).

Thanks to [exsilium](https://github.com/bertrandom/snowball-thrower/pull/1) for improving the command structure, optimizing the waiting times, and handling the failure scenarios. It can now run indefinitely!
