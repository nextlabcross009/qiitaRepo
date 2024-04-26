---
title: FactorioModを作ろう　Lua基礎
tags:
  - Lua
  - Factorio
private: false
updated_at: '2024-04-01T08:03:24+09:00'
id: ee17a5ac4d88aa09ec5e
organization_url_name: null
slide: false
ignorePublish: false
---
## Luaとは
スクリプト言語。さまざまなゲームにつかわれている。ガベージコレクションも搭載。基本上から下にプログラムが読まれていくので、関数の順に注意する必要がある。
変数は非常に柔軟だが悪く言えば型がないため少し使いにくいことも。

## 基本
コメント
```
--こめんと
--[[
複数こめんと
複数こめんと
--]]

```
Nullはnilになる。

ファイル内のみの参照はlocal

入れるもので型が変わる、柔軟
```
-- 数値の定義
local num = 10

-- 文字列の定義
local str = "Hello Lua!"
```
配列は基本tableで行う
```
-- テーブル（Luaの基本的なデータ構造）の定義
local table = {key1 = "value1", key2 = "value2"}
```
```
-- 基本的な算術演算
local sum = num + 10
local mul = num * 2

-- 文字列の連結
local greeting = str .. " Welcome to programming."

-- テーブルからの値の取得
local value1 = table.key1
```

条件分岐
```
local age = 20

if age < 18 then
    print("未成年です。")
elseif age >= 18 and age < 65 then
    print("成人です。")
else
    print("高齢者です。")
end
```

関数
```
local function Add(a, b)
    return a + b
end

local result = Add(5, 3)
print("結果: " .. result)
```
複数戻り値
```
function MinMax(a, b)
    if a < b then
        return a, b
    else
        return b, a
    end
end
local min, max = MinMax(10, 5)
print("Min:", min, "Max:", max)  -- Min: 5 Max: 10 を出力

```
配列としても受け取れる
```
local results = {MinMax(3, 7)}
print("Min:", results[1], "Max:", results[2])  -- Min: 3 Max: 7 を出力

```
luaの配列は1,2とあっても数字として扱っていない。すべて１（いち）という場所
に格納している。
なので基本的にはListで扱っていると思ったほうがいい。

繰り返し
```
-- for文による繰り返し
for i = 1, 5 do
    print("繰り返し回数: " .. i)
end

-- while文による繰り返し
local i = 0
while i < 5 do
    i = i + 1
    print("Whileループ: " .. i)
end
````
Tableの繰り返しこれはよく使う
```
local fruits = {apple = "red", banana = "yellow", grape = "purple"}

for key, value in pairs(fruits) do
    print(key .. ": " .. value)
end
```
tableの操作 追加
```
local fruits = {"apple", "banana", "grape"}

-- 末尾に要素を挿入
table.insert(fruits, "orange")

-- 2番目の位置に要素を挿入
table.insert(fruits, 2, "mango")

for i, fruit in ipairs(fruits) do
    print(i .. ": " .. fruit)
end
```
削除
```
-- 3番目の要素を削除
table.remove(fruits, 3)

for i, fruit in ipairs(fruits) do
    print(i .. ": " .. fruit)
end
```
要素数の確認　#をつける
```
local count = #fruits
print("Fruits count: " .. count)
```

## 表記
これはいろんな意見があると思うがとりあえず一例
関数変数
hoge_hoge

local は小文字始まり

ファイル名もhoge_hoge_hoge.lua

関数名
publicな関数は.をつけて表記する
ファイル名.関数名
function Blackbox.BlackboxInit()

## ほかにあってLuaにないもの
ないので工夫する必要がある
enum
class
switch文

## 発展
### プロトタイプ宣言
publicを上、privateは下の順にした場合。変数に関数をいれてプロトタイプ宣言のようにする必要がある。
FunctionPrototypeに関数を格納することでpublicな関数にて使用できる。
```
-- ローカル関数のプロトタイプ宣言
local FunctionPrototype

--public変数で使用
function()
    FunctionPrototype(5, 3)
end
-- ローカル関数の定義
FunctionPrototype = function(parameter1, parameter2)
    -- 関数の本体
    local result = parameter1 + parameter2
    return result
end

-- ローカル関数の使用
local result = FunctionPrototype(5, 3)
print("結果:", result)

```
### ファイルの読み込み　import
```
local Blackbox = require("blackbox")
--使用箇所
Blackbox.BlackboxInit()
```
### クラスとして使う
ベースとなるクラス
```
-- ベースとなるプロトタイプ（Animal）の宣言
Animal = {name = "unknown", sound = "not specified"}

-- AnimalのメソッドmakeSoundの定義
function Animal:makeSound()
    print(self.name .. " says " .. self.sound)
end

-- Animalをプロトタイプとして継承する新しいオブジェクト（Dog）を作成する関数
function Dog(name)
    local dog = {name = name, sound = "woof"}
    setmetatable(dog, {__index = Animal})
    return dog
end
```
クラス作成、コンストラクタ
```
local myDog = Dog("Rex")
myDog:makeSound()  -- "Rex says woof" と出力される
```
### enum
```
    global.EN_black_Box_entity_St = {
        None = 1,
        InPreparation = 2,
        InOperation = 3,
        Stop = 4,
    }
```
使用箇所
```
    if state == global.EN_black_Box_entity_St.None then

        return
    elseif state == global.EN_black_Box_entity_St.InPreparation then
        return
    elseif state == global.EN_black_Box_entity_St.InOperation then
        return
    elseif state == global.EN_black_Box_entity_St.Stop then
        return
    else
        return
    end
```
