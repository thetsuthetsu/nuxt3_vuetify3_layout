# Nuxt3, Vuetify3で基本的なレイアウトを構成

## vuetify3導入 (mdi/font, sass)

    ```
    $ yarn add -D vuetify@next @mdi/font sass
    ```
    
## vuetify3設定
* plugins/vuetify.ts

    ```
    import { createVuetify } from "vuetify";
    import * as components from "vuetify/components";
    import * as directives from "vuetify/directives";

    export default defineNuxtPlugin((nuxtApp) => {
    const vuetify = createVuetify({
        components,
        directives,
    });

    nuxtApp.vueApp.use(vuetify);
    });
    ```

* nuxt.config.ts
    ```
    // https://nuxt.com/docs/api/configuration/nuxt-config
    export default defineNuxtConfig({
    ssr: false,
    css: ["vuetify/styles", "@mdi/font/css/materialdesignicons.css"],
    })
    ``` 
    
## デフォルトレイアウトによる基本レイアウト構築
* レイアウト目標
    * ヘッダー
        * アプリケーションバー
        * 左ナビゲーションドローワー
            * railによるメニュー縮小
            * ３階層のメニュー
    * フッター
    * メインコンテンツ 

![](./images/nuxt3_vuetify3_menu.png)

    
* layouts/default.vue
    ```
    <template>
    <v-app>
        <AppHeader />
        <v-main>
        <v-container>
            <slot />
        </v-container>
        </v-main>
        <AppFooter />
    </v-app>
    </template>  
    ```
    
* components/AppHeader.vue
    * ヘッダーとドローワーメニューを定義
        * ヘッダー、ドローワーメニューで変数drawerを共有するため、同一コンポーネントに実装。
* components/AppFooter.vue 
    * フッター定義
        
* pages/index.vue
    ```
    <template>
        <div>
            <h1>Welcome to the homepage</h1>
        </div>
    </template>
    ```    