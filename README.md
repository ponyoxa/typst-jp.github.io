# Typst 日本語ドキュメント (※非公式)

組版システム [Typst](https://github.com/typst/typst) の非公式日本語ドキュメントです。[中国語版](https://github.com/typst-doc-cn/typst-doc-cn.github.io)からフォークして作成されました。

Web 版は次の URL から閲覧できます。
- Web 版: https://typst-jp.github.io/docs/

## 翻訳に参加するには

1. この GitHub リポジトリをフォークします。
1. ドキュメントの実体は、以下の2種類のファイルから構成されています。
    - Typst の言語リファレンスは、`./docs/i18n/**` 内の Yaml ファイルが実体です。これらを日本語に訳す時は、ファイル名の末尾が `-ja.yaml` となるようにしてください。
    例えば、https://typst.app/docs/reference/model/ を翻訳する際は、`./docs/i18n/category/model-en.yaml` を `./docs/i18n/category/model-ja.yaml` にコピーして翻訳してください。**既存の Yaml ファイルを直接書き換えて翻訳してはいけません**。
    - Typst のチュートリアルや入門ガイドなど、言語リファレンス以外のページは `./docs` 内の Markdown ファイルが実体です。**既存の Markdown ファイルを直接書き換えて翻訳してください**。
1. 「サードパーティ パッケージ」のページの翻訳を追加する場合は、`./static/assets/index2ja.json` も編集する必要があります。
1. 翻訳の際は、以下のガイドラインを遵守するようにしてください。
    1. 和文と欧文の間には半角スペースを挿入すること。
    2. 句読点は「, .」ではなく、和文の「、。」を使用すること。
    3. 不明な用語については、用語集または他のページの翻訳も参照すること。必要に応じて、Discord サーバ (後述) や Issue で相談すること。
    4. Typst の記述例の中に出てくる英文は、日本語に翻訳する必要はありません。
1. 翻訳作業が終わったら、Pull Request を送信してください。
1. 必要に応じて、文書の最後に翻訳者の名前を残すこともできます。

ご質問などがある場合は、[「くみはんクラブ」のDiscordサーバー](https://discord.gg/9xF7k4aAuH)に参加してご連絡ください。

もちろん、Discord サーバに参加していない方からの Pull Request も大いに歓迎します。

## 技術的な詳細

[中国語版](https://github.com/typst-doc-cn/typst-doc-cn.github.io?tab=readme-ov-file#%E6%8A%80%E6%9C%AF%E7%BB%86%E8%8A%82)参照

## ローカル環境でドキュメントを生成する

変更した Markdown/Yaml ファイルから、ローカル環境で Web サイトのデータを生成することも可能です。翻訳の際にこの作業は必須ではありませんが、書き換えたファイルが Web ページとして正しく表示されるのか確認するのに役立ちます。

まず、このリポジトリのクローンを作成し、`cargo` ツールチェーン、Python および Python パッケージの `jinja2` と `pyyaml` をインストールする必要があります。
```
# `./docs` 以下のディレクトリを変更した場合は、次の 2 行のコマンドを実行する必要があります
cargo test --package typst-docs --lib -- tests::test_docs --exact --nocapture
# `./docs/i18n` ディレクトリのみを変更した場合は、このコマンド行を実行するだけで済みます
python ./gen.py
```

最終的にコンパイルされたファイルは `./dist` にあります。

nodejs がインストールされている場合は、Web 静的サーバーをローカルですばやく起動し、`npxserve ./dist` を通じて結果をプレビューできます。
