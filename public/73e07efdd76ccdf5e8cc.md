---
title: Unity Androidの画面差（アスペクト比）に対応する
tags:
  - Unity
private: false
updated_at: '2024-02-22T12:12:27+09:00'
id: 73e07efdd76ccdf5e8cc
organization_url_name: null
slide: false
ignorePublish: false
---
## やりたいこと
スマホの画面の大きさに合わせて縦横が自動で調節される

## 細かいことはいいからやり方教えて
スクリプトを作成、設定
新規クラス、executeAlways属性追加
```
    [ExecuteAlways]
    public class CameraAspectKeeper
```
```
        private void Update()
        {
            float screenAspect = Screen.width / (float)Screen.height; //画面のアスペクト比
            float targetAspect = aspectVec.x / aspectVec.y; //目的のアスペクト比

            float magRate = targetAspect / screenAspect; //目的アスペクト比にするための倍率

            var viewportRect = new Rect(0, 0, 1, 1); //Viewport初期値でRectを作成

            if (magRate < 1)
            {
                viewportRect.width = magRate; //使用する横幅を変更
                viewportRect.x = 0.5f - viewportRect.width * 0.5f;//中央寄せ
            }
            else
            {
                viewportRect.height = 1 / magRate; //使用する縦幅を変更
                viewportRect.y = 0.5f - viewportRect.height * 0.5f;//中央余生
            }

            targetCamera.rect = viewportRect; //カメラのViewportに適用
        }
```
Mainのカメラをアタッチ　解像度を入力
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/1bbe75ae-0c6c-373e-ea68-c96054e9fed1.png)

MainCameraのBackGroundを黒で塗りつぶす。
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/9dffce77-ccf5-62d5-ce5d-070bcf2ea649.png)


UIの設定
CanvasのCanvasScalerを下記に変更
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/9fc5a8a8-c699-1d9e-ef7b-ca64d9ef65a8.png)

以上
Game画面でFreeAspectに画面を変えてみると確認できる。

## 補足
executeAlways属性はゲームの実行時でなくてもInspectrorの値が変更される。
実行していない時にGame画面を調整するとCameraのViewRectが変化する。
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/01a9b1e9-2344-6c85-790b-3eb736c688de.png)

機能の仕組み
画面の大きさに合わせてCameraのViewRectを変化させることで画面のアスペクト比を固定で変化させている。


## 参考サイト

https://3dunity.org/game-create-lesson/clicker-game/mobile-adjustment/

https://qiita.com/kiku09020/items/7c4a66d6c8ea7c500a09

