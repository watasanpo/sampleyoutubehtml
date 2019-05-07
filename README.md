# sampleyoutubehtml


## 今回できるもの

YouTubeを自分のサイトに表示させる方法について記述します。

iframeタグを使用します。

jqueryは不要です。

## チャレンジ

まずはYouTubeに動画を投稿します。

今回はすでに投稿された動画を使用します。

ブラウザーより

[https://www.youtube.com/watch?v=jNQXAC9IVRw](https://www.youtube.com/watch?v=jNQXAC9IVRw)

開きます。
 
共有　をクリックします。

埋め込む　をクリックします。

動画の埋め込みが表示されたら、プレーヤーのコントロールバーを表示するにチェックがあることを確認します。

コピー をクリックします。

タグがコピーされたら完了です。

```
<iframe width="560" height="315" src="https://www.youtube.com/embed/jNQXAC9IVRw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
```

タグをhtmlに貼り付けて完了です。

## 他のやり方

公式サイトより、

[https://developers.google.com/youtube/youtube_player_demo](https://developers.google.com/youtube/youtube_player_demo)

タグを修正します。

プレーヤーのコントロールを表示　をクリックします。

? をクリックして解説を見ながら値を変えます。

設定が完了したら、選択したオプションを使用してプレーヤーを更新をクリックします。

```
<iframe id="ytplayer" type="text/html" width="720" height="405"
src="https://www.youtube.com/embed/M7lc1UVf-VE?autoplay=1&controls=0&disablekb=1&enablejsapi=1&fs=0&loop=1&modestbranding=1&iv_load_policy=3"
frameborder="0" allowfullscreen>

```

`https://www.youtube.com/embed/M7lc1UVf-VE`の`M7lc1UVf-VE` が表示したい動画で変わります。

`Google Chrome` の バージョン: 73.0.3683.103では、バージョンでは、自動再生されません。

よって対応します。

`src="https://www.youtube.com/embed/M7lc1UVf-VE?`に`mute=1&` を追記します。

結果

```
<iframe id="ytplayer" type="text/html" width="720" height="405" src="https://www.youtube.com/embed/M7lc1UVf-VE?autoplay=1&controls=0&disablekb=1&enablejsapi=1&fs=0&loop=1&modestbranding=1&mute=1&iv_load_policy=3&rel=0&showinfo=0" frameborder="0" allowfullscreen></iframe>
```

にします。

w3c バリデート対応

[https://validator.w3.org/#validate_by_input](https://validator.w3.org/#validate_by_input)

htmlを貼り付けて検査

The frameborder attribute on the iframe element is obsolete. Use CSS instead.

frameborder属性は古い記述方法です。代わりにcssを使用します。

frameborderを消します。

Attribute type not allowed on element iframe at this point.

 type="text/html" 属性はiframeでは使用できません。

なので削除します。

続いてレスポンシブ対応します。

iframeタグをdivタグを挟みます。

class属性にyoutubeとして登録します。

htmlは、

```
    <div class="youtube">
        <iframe id="ytplayer" width="720" height="405" src="https://www.youtube.com/embed/M7lc1UVf-VE?autoplay=1&controls=0&disablekb=1&enablejsapi=1&fs=0&loop=1&modestbranding=1&mute=1&iv_load_policy=3&rel=0&showinfo=0" allowfullscreen></iframe>
    </div>
```

cssは、

```
.youtube {
    position: relative;
    padding: 52.65% 0 0 0;
    width: 100%;
}

.youtube iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}

```

.親要素youtubをewidthを100%にすることで、ブラウザー横幅に応じて
変化できるようにします。

padding で52.65%にする理由

youtubeの埋め込み動画の縦横比[アスペクト比](https://developers.google.com/youtube/youtube_player_demo?hl=ja)は16:9を基準に、横幅100%とした時の高さは、`9 / 16 * 100 =52.65%`になります。

子要素iframeで`position: absolute; top: 0; left: 0;`とする理由

`position: absolute; top: 0; left: 0;`とすることで親要素youtuveに重ねることができます。




でブラウザーで確認して終わりです。終わりです。




