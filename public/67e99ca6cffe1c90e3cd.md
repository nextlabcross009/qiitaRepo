---
title: Cursor(VsCode)のフォント「こいつ」の色を変更する。
tags:
  - VSCode
  - cursor
private: false
updated_at: '2024-04-11T17:23:53+09:00'
id: 67e99ca6cffe1c90e3cd
organization_url_name: null
slide: false
ignorePublish: false
---
こいつの色を変えたいという時のやり方。例えばクラス、変数・・・

ctrl + shift + P
Developer: Inspect TM Scopesで検索

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/de5f7d4e-0579-d357-f421-e7b2bc7b4b71.png)

変えたいものをクリック

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/fe8751fd-805b-9fb6-424f-68cccc3b96d8.png)

scopesを覚えておく

Settings.json
```
    "editor.semanticHighlighting.enabled": false,
```
他のテーマで上書きされないように設定
スコープと色を設定。

```
    "editor.tokenColorCustomizations": {
        "textMateRules": [
            {
                "scope": [
                    "entity.name.type.cs", // C# のクラス名に使用されるスコープ
                    "source.cs",
                ],
                "settings": {
                    "foreground": "#0de2a2" // GameObjectで使われている色
                }
            },
        ]
    },
```

色の変更完了。やったね。

追記、私の設定を貼り付ける

```
    "editor.semanticHighlighting.enabled": false,

    "editor.tokenColorCustomizations": {
        "textMateRules": [
            {
                "scope": [
                    "entity.name.type.cs", // C# のクラス宣言
                ],
                "settings": {
                    "foreground": "#0de2a2" 
                }
            },
            {
                "scope": [
                    "entity.name.type.class.cs", // C# のクラス名に使用されるスコープ
                ],
                "settings": {
                    "foreground": "#1bfbf3" 
                }
            },
            {
                "scope": [
                    "variable.other.object.property.cs", // 変数
                    "entity.name.variable.local.cs", //ローカル変数
                    "punctuation.squarebracket.open.cs",
                    "variable.other.readwrite.cs", //メンバ　使用箇所
                    "variable.other.object.cs", //メンバ　引数
                    "entity.name.variable.parameter.cs",//関数引数
                ],
                "settings": {
                    "foreground": "#d4d4d4" 
                }
            },
            {
                "scope": [
                    "keyword.operator.logical.cs", // &&
                    "keyword.operator.arithmetic.cs", // + -
                    "keyword.operator.relational.cs",// <>
                    "keyword.operator.assignment.cs", //=
                    "keyword.operator.comparison.cs",// ==
                    "keyword.operator.increment.cs",// ++
                    "keyword.operator.conditional.question-mark.cs",// ?
                    "keyword.operator.conditional.colon.cs",// :
                ],
                "settings": {
                    "foreground": "#c694ff"
                }
            },
        ]
    },
```
