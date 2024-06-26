---
title: 始めようゲーム制作：すいのゲームを作ろう（第2回）
tags:
  - Unity
  - ゲーム制作
  - すいのゲームを作ろう
private: false
updated_at: '2021-12-11T13:51:04+09:00'
id: c99fdfc8aa64c95d8c2d
organization_url_name: null
slide: false
ignorePublish: false
---

#ゲーム流れ
さあ、ゲーム作りを始めよう！といいたいところですが、まずはゲーム作りの一連のやることリストを確認してみましょう。リストはエクセルにて管理しています。
![スクリーンショット 2021-12-11 130632.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/c67c9dcc-907e-b6a2-6d12-9a0753a810e8.png)
どれだけかかったを管理することで次回作を作る時、どれだけ時間が掛かるのかの目安となります。
ものによってかかる時間も様々ですが見ての通りやるこが多いですね。なによりもあきらめないことがゲーム作りで大切な要素だと思っています。

#ゲーム企画しよう
では実際にゲーム作りを始めましょう。まずはどんなゲームするかです。なんでもいいですが個人ゲーム開発なのでとにかく簡単につくれるものがいいです。自分が簡単に作れると思っているゲームでもいざ作ってみると簡単にはつくれないです。とにかく簡単に、簡単にを心がけます。まず作ってみて、作ったゲーム遊びながら面白い要素を足していくやり方がいいと思っています。

とりあえず今、私は英語に興味をもっています。なので英語に関係するゲームを作ろうと思います。英語のゲームを1から考えても良いと思いますが、おすすめはテーマが決まればそのテーマで検索して同じテーマのゲームを遊んでみることです。遊んでみて面白いところや、ゲームバランス、作風等学ぶべきところがたくさんみつかると思います。そのうえで自分のゲームを考えると良いでしょう。

その後、自分のアイディアを出して形にしていきます。最近だとIpadを利用し、始めのイメージを考えます。Conceptsというアプリは無限にキャンパスの大きさが広げることができるので、アイディアを出すには適しています。始めのイメージはこんな感じにしました。
![アップルランイメージ.jpg](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2294598/ba17f1d1-b309-710b-a9df-1a3d08a6d428.jpeg)

リンゴが道を走っていって、Appleと書かれたテープや木を通りぬけるゲームになります。もしOrengeと書かれていたら下のボタンを押して走っている果物をきりかえます。果物と文字同じであれば通り抜けることができ異なっているとゲームオーバーとなります。単語と絵を様々用意することで、拡張性もありそうです。

#ゲームの手触り
ゲームでは手触りがとても大切です。手触りとは遊んでいて楽しいと感じる感覚です。例えばジャンプ一つにしてもそのジャンプがマリオのように空中で移動できるものなのか、それとも魔界村のように移動ができないものなのか、そしてそのジャンプの速さ、高さ、様々な要素で成り立っています。その中で楽しいと感じる感覚を選ばなければなりません。

人は快感を感じる感覚があります。イージングのなかでもeaseInOutExpoやeaseoutCircといった、あるしきい値を超えた時に勢いよく変化するものに快感を感じます。身近の物でボタンのクリック感がそれにあたります。
特にアクションゲームはそういう細かい部分の調整がされているので自分で研究して見ると面白いと思います。
今回の私のゲームでも、文字が書いてあるラインを通り抜けるときにプチンとちぎれるのような感覚を表現出来たら楽しいのではないかと考えました。



