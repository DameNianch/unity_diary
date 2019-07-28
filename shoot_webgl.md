# 最終的にできるようにしたいこと
## 最強の対オレゲームキャラ作成
- ゲームは何でもいい
- ゲーム画面のデータ取得・保存
- tensorflowで強化学習したモデルの読み込み


# 他人のコードをパクる
## パクり方のステップ
1. unityで使うソースコードが入ったフォルダを頂く
    - この中にはAssets, ProjectSettings等が入っている。
1. unity hubのリストに追加からフォルダを選択
1. プラットフォームを選択（今回はWebGL）
1. 必要ならば画面サイズ調整
- 感想
    - ProjectSettingsの中にassetが入ってるのだが、どういう構成？
    - 保存箇所ってどこにすればいいのだろうか？（デフォルトのAssetsに保存した。）
- 参考
    - [チュートリアル2Dシューティング](https://unity3d.com/jp/learn/tutorials/projects/2d-shooting-game/getting-started?playlist=46524)

## WebGLとは
- 

## プレイヤーの基礎制御
- 用語
    - アタッチ
        - コンポーネントをオブジェクトに与えること。今まで適用と勝手に命名してた行為のこと。3種類の方法がある。
    - Apply Root Motion
        - 3Dモデルの制御をいい感じにする何か。2Dの時はoffにする必要がある。

- 基本事項
    - 移動入力
        1. Input.GetAxis~でキー入力（ベクトル）を取得
        1. ベクトルの正規化
        1. キー入力に対して定数をかける（スピード一定）
    - ミサイル（複数）発車
        1. Spritesに画像を用意
        1. 複数のミサイルが従う親オブジェクトを作成、子オブジェクト化
        1. 親子をPrefab化
        1. いい感じのスクリプトをアタッチ
        1. public変数でPrefab変数（？）を用意して対象をインスタンス化
        1. publicの対象をミサイルのPrefabにする

- 問題
    - camera
        - Main Cameraのsizeは縦方向のグリッド数？
        - Camera.main.ViewportToWorldPointのmainってどうやって決まった？
- その他
    - _Completed-Assetsに完成しているっぽいスクリプト等が全て有り
    - GetComponentの対象はジェネリックで決めているということ？


    - 画面外に移動させたくない場合
        - カメラの描画範囲を取得
        - その範囲外に出ないようMathf.Clampを使用