---
title: Unity UI チャットのような下から上へ流れるテキスト表示のやり方
tags:
  - Unity
private: false
updated_at: '2024-02-27T21:57:23+09:00'
id: fe8a8066cff2117bdceb
organization_url_name: null
slide: false
ignorePublish: false
---
なにはともあれCreate>UI>ScrollViewを追加
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/86149f6b-1b20-38b0-5283-92a8a4f283fc.png)
CntentにVertial Layout Groupの追加
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/8219bec2-fabb-6394-7598-6ca786e6b48f.png)
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/d95612df-ebb4-3fba-b93f-083a7719b007.png)

Contentの子にしてTextを追加
Hierarchy右クリック>UI>Text

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/fa4c494c-030e-4c33-6ce1-35742e726f2f.png)
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/82e31e23-3027-9700-4222-539d271937f6.png)

追加したTextとコピペするとViertial Layout Groupの影響で縦に並ぶ
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/ff423525-8635-ceed-3cf0-02ae307d48a1.png)

きれいならばないときはSpacingを調整してみる
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/372fbf98-f714-b931-45a0-f46a50374e76.png)
一度動かしてみる
![Listugokasi.gif](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/77f2ba3b-1771-ca74-c089-322c87fa722d.gif)

ここからがやっかいだかすべて必要になる
ContntのPivotのYを0に
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/394c6ce3-78a8-5b25-560b-49a2ffe652bf.png)
ContentにContentSize Filterを追加
VerticalLayoutGroupとContentSizeFilterの値を画像のとおり設定

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/f2ddea0a-c8c3-f673-325d-71fbc44f5836.png)

Contentの子にTextを追加
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/471e4c0b-9bd1-fe61-6def-ef3fdef93094.png)
下側に追加される
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/31af60eb-e7e1-dd8c-f8c2-148f466ddf71.png)

ここからスクリプト
適当なの作成

```
using UnityEngine;
using UnityEngine.UI;
using TMPro;

public class ScrollViewTest : MonoBehaviour
{
    [SerializeField] private ScrollRect scrollRect;
    [SerializeField] private GameObject addObj;
    [SerializeField] private GameObject parentObj;

    // Start is called before the first frame update
    void Start()
    {

    }

    // Update is called once per frame
    void Update()
    {
        
    }
    public void AddText()
    {
        var Obj = Instantiate(addObj, parentObj.transform);
        Obj.GetComponentInChildren<TMP_Text>().text = Random.Range(0, 100).ToString();
        scrollRect.verticalNormalizedPosition = 0;
    }
}
```

TMPじゃなければTextに修正して
addObj：追加するテキストObject
ParentObj:親のObject。addObjを追加していく
scrollRect：ScrollViewのScrollRectcomponentを参照させる

![Listugokasimove.gif](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/12897c6f-2d66-a708-1540-ef525eb1e70c.gif)

ButtonでもなんでもAddTextを呼び出す
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/e8729a67-6d4c-df66-8b8e-b9f6d4b7b30f.png)

動かしてみると
![Listugokasimovefew.gif](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/9885d504-8360-d33d-9847-7537b9243037.gif)

したから上にテキストが動いてチャットのような挙動になる。
やったね。

