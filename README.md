# VideoEncoderDecoder

# 概要
本プロジェクトでは、動画の前景・背景を動きの特徴に基づいてセグメント化し、それぞれ異なる圧縮率で処理することで、映像の品質とデータ圧縮率のバランスを最適化します。

プロジェクトは以下の2つのプログラムで構成されます：
1. エンコーダ (MyEncoder.exe)
入力されたRGB動画に対して、16×16ピクセルのマクロブロック単位で動きベクトルを算出します。
動きベクトルの一貫性と隣接性に基づき、前景と背景を分類します。
各マクロブロックをさらに8×8ブロックに分割し、DCTを適用します。
前景と背景ごとに異なる量子化パラメータ（n1: 前景, n2: 背景）でDCT係数を量子化し、圧縮ファイル (.cmp) に保存します。

2. デコーダ (MyDecoder.exe)
圧縮ファイル (.cmp) を読み込み、マクロブロックの種類に応じて適切な逆量子化と逆DCTを行い、画像を復元します。
指定された音声ファイル (.wav) と同期させた独自のA/Vプレイヤーで再生します。プレイヤーは再生、停止、一時停止、フレーム単位での再生制御をサポートします。

# 入力コマンド
MyEncoder.exe input_video.rgb n1 n2
MyDecoder.exe input_video.cmp input_audio.wav

# リンク
Demoを見る
https://youtu.be/JuKcR8gyRwE

コード(Release版のZIPファイルの中に input file が含まれています。)
https://github.com/naokyan/VideoEncoderDecoder
