<h1 align="center">ぶいらじ</h1>

<p align="center"><b>VRChat・VR機器・XRのニュースと、アバター・衣装・ギミックの新作とセールを、毎日お届け。</b></p>

<p align="center">
  <a href="https://lazyrabbit417-star.github.io/buiraji/"><img src="https://img.shields.io/badge/%E2%96%B6%20ON%20AIR-%E3%81%B6%E3%81%84%E3%82%89%E3%81%98-ffd028?style=for-the-badge&labelColor=ff4468" alt="ぶいらじを見る"></a>
</p>

キャラクターがVRのニュースを読む、HTMLのラジオ番組です。再生に合わせて、スライド・字幕・キャラ・記事のリンクカードが動きます。

- 番組を見る：<https://lazyrabbit417-star.github.io/buiraji/>
- 台本は `episodes/` に文字で残っています。過去の回も、記事として読めます

## 番組の作り方

1. **台本を書く**：`episodes/<日付>-ja.json`。ニュースごとに見出し・要点・話す文・出典。形は [docs/formats.md](docs/formats.md)
2. **リンクカード**：`python tools/linkcard.py <記事のURL> ...` で、記事の共有用画像（OGP）とタイトルを集める
3. **声を吹き込む**：COEIROINK を起動して `python tools/voice.py episodes/<日付>-ja.json`。`audio/` に mp3 ができ、字幕のタイミングと `episodes.json` も更新される
4. **手元で見る**：`python tools/serve.py` を動かして <http://127.0.0.1:8765/> を開く（Python 標準の `http.server` だと音声の途中へ移れず、見出しを押しても最初から再生されるので、こちらを使う）
5. **放送する**：`main` にコミットして push し、`bash tools/publish-win.sh` を実行（Windows の Git Bash で。中で `tools/publish.sh` を動かす）

音声は `main` にはコミットしません。`tools/publish.sh` が、直近 30 日分の音声だけを `gh-pages` ブランチに載せます。

## クレジット・ライセンス

- 声：COEIROINK:リリンちゃん
- キャラ：[myradio](https://github.com/monoradio102/myradio) のお手本のキャラ（AIで生成したキャラクター。公序良俗に反しない使い方なら自由に使えます）
- プレーヤー（`index.html`、`tools/`）：[myradio](https://github.com/monoradio102/myradio) をもとにしています。MIT License
- 台本（`episodes/`、`episodes.json`）：CC0
- 天気：Open-Meteo（CC BY 4.0）
- ニュースの画像は、記事のサイトが共有用に公開している画像（OGP）を、そのサイトから直接表示しています
