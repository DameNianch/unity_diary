# 最終的にできるようにしたいこと
## 最強の対オレゲームキャラ作成
- ゲームは何でもいい
- ゲーム画面のデータ取得・保存
- tensorflowで強化学習したモデルの読み込み


# unityインストール
- 参考ページ：https://uni.gas.mixh.jp/unity/mac-install.html
- 結果：unity hubの選択肢のみ
- 決断：unity hubを選択
- 感想：macだからunity hubしかないんかな、、、

# unity入門
## 基本事項
- 参考ページ：https://unity3d.com/jp/learn/tutorials/projects/hajiuni/creating-a-project?playlist=45986
- 問題
    - プロジェクト作成のUIが異なる
        - プロジェクトが作れたので問題なかったことにした
    - Layoutの選択不可
        - デフォルトで2by3等が入っていない。
        - 自力でセットして保存
- 感想
    - project, hierarchy, inspectorの順に細かくなってるから、2by3の順序は微妙な気がする。
    - ビューの動かし方は、覚えられる自信がないのでやりながらなんとかする。
    - テキストサイズが小さくて若干辛い

## ゲームオブジェクト作成

### ゲームオブジェクトとは
- スクリプトで処理する何か全般
    - ボールや壁
    - 効果音やトリガー（？と呼ばれる何か）
- 感想：panelじゃなくてplaneかな？
- z軸は天井に向かっていない。yが天井に向かっている。
- 用意したオブジェクトをInspectorにあるチェックを外すことで消すことも可能

### 材質の決定
1. ProjectからMaterialを作成
1. Inspectorから調整
1. ドラッグ&ドロップでゲームオブジェクトに適用

### オブジェクト配置
- 問題
    - Vを押しながら移動してもいい感じにしてくれない。
        - おそらくcommand+v
- 感想
    - albedoってググった時のwikipediaと画像の不一致やめてくれぇ（スペル間違えたかと思った。）
    - default checkerだと適用されたかどうか分からんからdefault checker greyを適用した
    - １つ1つのゲームオブジェクトに適用しているけどグルーピングしていい感じにまとめて適用したい。

### オブジェクトの管理
- emptyという空のオブジェクトにまとめておく。
- emptyに性質を持たせることでメリット
    - staticにすることができるならば変更

### 材質の管理
- フォルダにまとめておく
- 問題
    - Emission値の選択肢が無いが、どういうことだ？
    - 参考：[ここ](https://unity3d.com/jp/learn/tutorials/projects/hajiuni/adding-obstacles-and-restart?playlist=45986)の「DengerWallの色を設定」
    - Intensityのこと？
- 感想
    - sceneと同じ階層に入れるのは、どういう意図があるのだろうか？


### オブジェクトへの機能追加
- コンポーネントというものを追加することでオブジェクトに性質を追加
- 複雑な機能の追加は、C#またはunity script
    - public変数を用いるとinscpectorから変数を変更可能
- 問題
    - C#が選べる前提の話だが、選択肢がなく自動でC#になった。
- 感想
    - セミコロンを忘れない。
    - これspeedじゃなくて加速度だろ


## カメラの移動

### カメラとは
- カメラはオブジェクト
- デフォルトでは、カメラは親オブジェクトに追従（たぶん）
    - 親オブジェクト：人間の親オブジェクトは地球。地球の親オブジェクトは太陽
    - コンポーネントを与えることで追従対象を変更することが可能

## Prefabの利用
### Prefabとは
- わからん
- 使うとオブジェクトを量産可能っぽい。
- Materialやscriptと同じくaseteと同じ階層
- Prefabにオブジェクトを追加、sceneにドラッグ&ドロップでコピーを量産

### コンポーネントの追加
- Prefabにあるオブジェクト（？）にコンポーネントを追加
- Prefabからコンポーネントを持ったオブジェクト（？）量産
- 問題
    - Prefabのオブジェクト（？）にMaterialを付与するスマートな方法が分からない。
        1. 一度、PrefabにItemMaterialを追加
        1. ItemMaterial付与
        1. ItemMaterialをMaterialフォルダに移動
    - 解決方法
         - ヒエラルキーにあるオブジェクトに適用してからapplyをするっぽい。（たぶん）
         - applyすると同じprefabから生成された全てのオブジェクトに反映

- 感想
    - 摩擦係数（？）無いと動かしにくい(壺おじさんかよ)
    - Drag=2に変更したらいい感じ

## その他技術

### UIの表示
- テキスト表示をしたが、あまり理解できていないので放置する。
- textオブジェクトはcanvasに自動追加
- textオブジェクトはcreateからUIで選択

### 明るさの調整
- Directional Lightの Intensityを調整
- Lightが弱くなるとIntensityの高いオブジェクトが光って見える

### シーンの扱い
- UnityEngine.SceneManagementクラスを利用
- 詳細は放置