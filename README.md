# priority-App

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

### Run Unit Tests with [Vitest](https://vitest.dev/)

```sh
npm run test:unit
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```


# 設計書
この設計では、Vue.jsをフロントエンドとして使用し、Supabaseをバックエンドデータベースとして活用します。

#### ディレクトリ構造

```
my-app/
  ├── public/
  │   ├── index.html
  ├── src/
  │   ├── assets/
  │   ├── components/
  │   │   ├── Home.vue
  │   │   ├── InputForm.vue
  │   │   ├── ViewData.vue
  │   ├── router/
  │   │   ├── index.js
  │   ├── services/
  │   │   ├── supabaseClient.js
  │   ├── App.vue
  │   ├── main.js
  ├── package.json
```

#### 各ファイルの説明

1. `index.html`: メインのHTMLファイル。
2. `Home.vue`: ホームコンポーネント。InputFormとViewDataコンポーネントを含む。
3. `InputForm.vue`: データ入力用の登録フォームコンポーネント。Supabaseにデータを保存する機能を持つ。
4. `ViewData.vue`: Supabaseからデータを取得し、画面に表示するコンポーネント。
5. `index.js`: Vue Routerを定義するファイル。ルート設定を含む。
6. `supabaseClient.js`: Supabaseクライアントの初期化とデータベース操作のメソッドを定義。
7. `App.vue`: メインのVueコンポーネント。ルータービューを含む。
8. `main.js`: Vueアプリケーションのエントリポイント。

#### 設計

1. `Home.vue`を作成し、`InputForm.vue`と`ViewData.vue`コンポーネントをインポートします。
2. `InputForm.vue`に入力フォームを実装し、データの送信ボタンを設置します。送信ボタンをクリックすると、入力されたデータがSupabaseに保存されるようにします。
3. `ViewData.vue`にデータ表示領域を実装し、Supabaseから取得したデータを表示します。データが更新されるたびに、表示も自動的に更新されるようにします。
4. `supabaseClient.js`を作成し、Supabaseクライアントを初期化します。また、データを保存するための関数やデータを取得するための関数を定義します。
5. `App.vue`で`Home.vue`コンポーネントをルータービューとして表示します。
6. `index.js`にVue Routerの設定を追加し、`Home.vue`をルートパス（`/`）にマッピングします。
7. `main.js`でVueアプリケーションを作成し、Vue Routerを使用するよ