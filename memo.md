# DotinstallPane Memo

## 07 疑似要素でサブタイトルを作ろう

「Dotinstall Paneの特徴」部分のセクション作成

### sectionタグの作成

```
[index.html]
<section class="features">
    <div class="container">
        <h1>Dotinstall Paneの特徴</h1>
    </div>
</section>
```

### section部分のスタイル作成

```
[style.css]
/* features */
.features h1 {
    text-align: center;
    font-weight: normal;
    font-size: 24px;
}
```

### サブタイトルの作成

[疑似要素](https://saruwakakun.com/html-css/basic/before-after)でサブタイトルを追加

```
[index.html]
<div class="container">
    <h1 data-subtitle="- Features -">Dotinstall Paneの特徴</h1>
</div>
```
```
[style.css]
.container {
    width: 820px;
    margin: 0 auto;
    padding: 60px 0;
}

.features h1::after {
    content: attr(data-subtitle);
    display: block;
    font-size: 16px;
    color: #aaa;
    padding-top: 10px;
}
```

## 08 スタイルを再利用できるようにしよう

前項で作成したスタイルは、別セクションでも共通で使うため再利用できるようにする。

### セクションタイトルにクラス追加

```
[index.html]
<div class="container">
    <h1 data-subtitle="- Features -" class="section-title">Dotinstall Paneの特徴</h1>
</div>
```

### セクションタイトルのスタイルを共通化


.feature h1部分を変更する。
また、共通化部分はCSSの上部に置くと良い。

```
[style.css]
/* features */
.section-title {
    text-align: center;
    font-weight: normal;
    font-size: 24px;
}

.section-title::after {
    content: attr(data-subtitle);
    display: block;
    font-size: 16px;
    color: #aaa;
    padding-top: 10px;
}
```

## 09 特徴紹介セクションを作ろう

特徴紹介の3つのセクションを作成する

### 1つ目の特徴のマークアップ

```
[index.html]
<div class="container">
    <h1 data-subtitle="- Features -" class="section-title">Dotinstall Paneの特徴</h1>
    <section class="feature">
        <img src="img/feature1.png"/ width="420" height="270" alt="特徴1">
        <div class="desc">
            <h1>すいごい特徴があるよ！</h1>
            <p>いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。</p>
        </div>
    </section>
</div>
```

### コピーして残りの特徴を作成

```
[index.html]
<div class="container">
    <h1 data-subtitle="- Features -" class="section-title">Dotinstall Paneの特徴</h1>
    <section class="feature">
        <img src="img/feature1.png"/ width="420" height="270" alt="特徴1">
        <div class="desc">
            <h1>すいごい特徴があるよ！</h1>
            <p>いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。</p>
        </div>
    </section>
    <section class="feature">
        <img src="img/feature2.png"/ width="420" height="270" alt="特徴2">
        <div class="desc">
            <h1>すいごい特徴があるよ！</h1>
            <p>いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。</p>
        </div>
    </section>
    <section class="feature">
        <img src="img/feature3.png"/ width="420" height="270" alt="特徴3">
        <div class="desc">
            <h1>すいごい特徴があるよ！</h1>
            <p>いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。いろいろあります。</p>
        </div>
    </section>
</div>
```

## 10 要素を左右に振り分けていこう

特徴要素を左右に振り分けする。

### feature内の要素のスタイル調整

```
[style.css]
/* features */
.feature h1 {
    font-weight: normal;
    font-size: 18px;
}

.feature .desc {
    width: 360px;
}
```

### 偶数奇数で左右分けする

nth-of-typeを使用して、偶数番目は説明文を右へ、奇数番目は説明文を左へ移動する。

```
[style.css]
.feature:nth-of-type(odd) .desc {
    float: right;
    padding-left: 40px;
}

.feature:nth-of-type(even) .desc {
    float: left;
    padding-right: 40px;
}
```

## 11 特徴紹介セクションを完成させよう

### セクションタイトルの余白調整

上下のマージンを指定

```
[style.css]
.section-title {
    text-align: center;
    font-weight: normal;
    font-size: 24px;
    margin-bottom: 60px;
    margin-top: 0px;
}
```

### 特徴部分の余白調整

「:not()」で引数以外の要素に適用される
引数の値に「:last-child」を指定することで、最終要素にステイルを適用出来なくできる

```
[style.css]
.feature:not(:last-child) {
    margin-bottom: 60px;
}
```

### 特徴の説明文がはみ出したときの対応

```
[style.css]
.feature {
    overflow :hidden;
}
```

## 利用者の声作成

利用者の声のマークアップを行います。

### 枠組み、タイトルの作成

特徴の流用をする

```
[index.html]
<section class="voices">
    <div class="container"></div>
<section>

[style.css]
/* voices */
.voices {
    background: #f8f8f8;
}
```

### 利用者の声を3つ作成する。

こちらも特徴と同じ構造で記述

```
[index.html]
<div class="container">
    <h1 data-subtitle="- Voices -" class="section-title">利用者の声</h1>
    <section class="voice">
    <img src="img/user1.png" width="90" height="90" alt="利用者A">
    <h1>利用者A</h1>
    <p>
        良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。
    </p>
    </section>
    <section class="voice">
    <img src="img/user2.png" width="90" height="90" alt="利用者B">
    <h1>利用者B</h1>
    <p>
        良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。
    </p>
    </section>
    <section class="voice">
    <img src="img/user3.png" width="90" height="90" alt="利用者C">
    <h1>利用者C</h1>
    <p>
        良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。
    </p>
    </section>
</div>
```

## Flexboxを使った配置

利用者の声をFlexboxを使って配置する。

### Flexbox用のコンテナ作成

flexboxクラスを持つdivタグでsectionタグを囲む

```
[index.html]
<div class="flexbox">
    <section class="voice">
    <img src="img/user1.png" width="90" height="90" alt="利用者A">
    <h1>利用者A</h1>
    <p>
        良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。
    </p>
    </section>
    <section class="voice">
    <img src="img/user2.png" width="90" height="90" alt="利用者B">
    <h1>利用者B</h1>
    <p>
        良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。
    </p>
    </section>
    <section class="voice">
    <img src="img/user3.png" width="90" height="90" alt="利用者C">
    <h1>利用者C</h1>
    <p>
        良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。良い感じです。
    </p>
    </section>
</div>
```

### flexboxのCSSを作成

```
[style.css]
.voices .flexbox {
    display: flex;
    justify-content: space-between;
}

.voice {
    width: 250px;
    background: #fff;
}
```

### voice内の要素の調整

```
[style.css]
.voice {
    width: 250px;
    background: #fff;
    position: relative;
}

.voice img {
    border-radius: 50%;
    border: 10px solid #fff;
    position: absolute;
    left: 0;
    right: 0;
    margin: 0 auto;
}
```

### 14 利用者の声セクションを完成させよう

利用者の声のデザインの微調整を行います。

### Flexbox内の調整

box-sizing、画像の位置の調整

```
[style.css]
.voice {
    width: 250px;
    background: #fff;
    position: relative;
    box-sizing: border-box;
    padding: 60px 40px 25px;
}

.voice img {
    border-radius: 50%;
    border: 10px solid #fff;
    position: absolute;
    left: 0;
    right: 0;
    margin: 0 auto;
    top: -55px;
}
```

Flexbox内のタイトルの調整

```
[style.css]
.voice h1 {
    text-align: center;
    font-size: 18px;
    font-weight: normal;
}
```

セクションタイトルのマージン調整

```
[style.css]
.voices .section-title {
    margin-bottom: 95px;
}
```

## 15_最後のセクションを作っていこう

call-to-actionのセクションを作成

### call-to-actionセクションのマークアップ

```
[index.html]
<section class="call-to-action orange-bg">
    <div class="container">
      <h1 class="section-title">Dotinstall Paneを使ってみよう！</h1>
      <a href="#" target="_blank" class="btn">詳細を見る <i class="fas fa-external-link-alt"></i></a>
    </div>
</section>
```

### call-to-actionセクションのスタイリング

```
[style.css]
/* call-to-action */
.call-to-action {
    text-align: center;
    margin-bottom: 15px;
}
```

## 16 ウェブサイトを完成させよう

フッターの作成

### フッターのマークアップ

```
[index.html]
<footer>
    <p>&copy; dotinstall.com</p>
</footer>
```

### フッターのスタイリング

```
[style.css]
/* footer */
footer {
    padding: 40px 0;
    text-align: center;
    color: #aaa;
}
```
