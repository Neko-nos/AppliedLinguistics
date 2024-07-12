# 0. 概要
本レポジトリは言語応用論の期末レポート用のものです。
## 0.1 ファイル説明
imagesフォルダに今回使用した写真が入っています。
`evovlm.ipynb`でEvoVLM-JP-v1-7Bによる実験が、`gemini.ipynb`でGemini 1.5 Flash latestによる実験が記載されています。

# 1. 環境構築
## 1.1 Pythonの仮想環境の設定
今回はpyenv + virtualenv + pipという構成をとっていますが、他のツールを使いたい場合は`.python-version`と`requiremnts.txt`を参照してください。以下では先に挙げた構成に基づいて説明を行います。

まず、作業したいディレクトリ(以下ではAppliedLinguisticsと呼ぶことにします)において本レポジトリをcloneします。<br>
`git clone https://github.com/Neko-nos/AppliedLinguistics.git` <br>
cloneしたくない場合はzipファイルをダウンロードできますのでそちらをご活用ください。

次にコードが置いてあるディレクトリに移動してPythonの仮想環境を作ります。
```Shell Script
virtualenv env
source env/bin/activate
```
次に、必要なライブラリをinstallします。
```Shell Script
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121
pip install -r requirements.txt
```
以上でPython側の環境設定は終了です。

## 1.2 モデルの準備
今回使うモデルは以下の3つです。
1. Gemini 1.5 Flash latest
2. EvoVLM-JP-v1-7B
3. Llama Guard2

まずは、これらの環境設定を行います。
### 1.2.1 Gemini 1.5 Flash latest
本レポジトリの作成時点(2024/7/8)では無料で使えます。以下のサイトの指示に従ってAPI Keyを作成してください。<br>
https://ai.google.dev/gemini-api <br>
次にAPI Keyを環境変数として扱えるように、作業ディレクトリ(AppliedLinguistics)にて`.env`ファイルを作成して、以下の内容を記載します。
```
GOOGLE_API_KEY={作成したAPI Key}
```
### 1.2.2 EvoVLM-JP-v1-7B
以下のサイトからモデルをダウンロードして、作業ディレクトリ(AppliedLinguistics)にてEvoVLM-JP-v1-7Bという名前でファイル達を配置します。
https://huggingface.co/SakanaAI/EvoVLM-JP-v1-7B
### 1.2.3 Llama Guard2
以下のサイトからモデルをダウンロードするのですが、まだ承認を受けていない場合は指示に従って承認を得ます(私は数分ぐらいで貰えた記憶があります)。<br>
https://huggingface.co/meta-llama/Meta-Llama-Guard-2-8B<br>
その後は先ほどと同様に、モデルをダウンロード後、作業ディレクトリ(AppliedLinguistics)にてMeta-Llama-Guard-2-8Bという名前でファイル達を配置します。

以上の環境設定を終えた後は`example.ipynb`を実行して適切に処理が行われているのを確認してください。
