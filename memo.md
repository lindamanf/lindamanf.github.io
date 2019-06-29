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

### コンテナスタイルの作成

```
[style.css]
.container {
    width: 820px;
    margin: 0 auto;
    padding: 60px 0;
}
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