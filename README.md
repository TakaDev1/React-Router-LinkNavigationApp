# React Router Link Navigation App

React Routerの`Link`を使用して、`Home`と`About`のページを移動できるナビゲーションを実装する練習アプリです。

## 概要

`Link`コンポーネントを使用して、URLを変更しながら`Home`と`About`を行き来できるようにします。

| URL      | ページ   |
| -------- | ----- |
| `/`      | Home  |
| `/about` | About |

## 学習内容

* `Link`の使い方
* `to`属性による遷移先の指定
* React Routerによるページ遷移
* `<a>`タグとの違い

## 条件

* `/` → `Home`
* `/about` → `About`
* `Link`を使用する
* `Home`へのリンクを作成する
* `About`へのリンクを作成する
* `<a>`タグは使用しない

## ディレクトリ構成

```text
src/
├── components/
│   └── Navigation.tsx
├── pages/
│   ├── Home.tsx
│   └── About.tsx
├── App.tsx
└── main.tsx
```

## 実装例

### Navigation.tsx

```tsx
import { Link } from "react-router";

const Navigation = () => {
  return (
    <nav>
      <Link to="/">Home</Link>
      <Link to="/about">About</Link>
    </nav>
  );
};

export default Navigation;
```

### App.tsx

```tsx
import { BrowserRouter, Route, Routes } from "react-router";
import About from "./pages/About";
import Home from "./pages/Home";
import Navigation from "./components/Navigation";

function App() {
  return (
    <BrowserRouter>
      <Navigation />

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

## `Link`の基本

`Link`の`to`属性に遷移先のURLを指定します。

```tsx
<Link to="/">Home</Link>
<Link to="/about">About</Link>
```

それぞれ、

```text
Home  → /
About → /about
```

へ遷移します。

## `<a>`タグを使用しない理由

React Routerでは、アプリ内のページ遷移に`Link`を使用します。

```tsx
<Link to="/about">About</Link>
```

一方、通常の`<a>`タグは、

```tsx
<a href="/about">About</a>
```

のように使用します。

React RouterによるSPAのルーティングでは、基本的に`Link`を使用してページ遷移を行います。

## 実行

```bash
npm install
npm run dev
```

ブラウザで以下にアクセスします。

```text
http://localhost:5173/
```

`Home`から`About`へ移動し、さらに`About`から`Home`へ戻れることを確認してください。

## 課題のポイント

この課題では、React Routerにおける基本的なナビゲーションを理解することを目的とします。

```text
Navigation
    ↓
Link
    ↓
URL変更
    ↓
Routes
    ↓
対応するページを表示
```
