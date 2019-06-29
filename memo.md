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