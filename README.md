# vite-plugin-monaco-editor-nls
monaco-editor Display language switching plugin

### Remark:
I encountered an issue with converting the display language when developing using monaco editor. Upon reviewing the documentation, I found that some experts had already developed the plugin, but it could not be successfully translated into Chinese according to the provided documentation. I separately wrote a separate plugin and found that some text displayed conversion failure. After debugging, I found that the plugin package was missing the required conversion data. I then consulted monaco editor nls to resolve the issue.

refer to

https://github.com/microsoft/monaco-editor/
https://www.npmjs.com/package/monaco-editor-nls
https://github.com/pearone/vite-plugin-monaco-editor-nls


### Install:

```shell
npm install vite-plugin-monaco-editor-nls
```

### Using

Add this plugin in vite.config.ts(.js)：

```typescript
import MonacoEditorNlsPlugin, {
    esbuildPluginMonacoEditorNls,
    Languages,
} from 'vite-plugin-monaco-editor-nls';

// https://vitejs.dev/config/
export default defineConfig({
    resolve: {
        alias: {
            '@': resolve('./src'),
        },
    },
    build: {
        sourcemap: true,
    },
    optimizeDeps: {
        /** vite >= 2.3.0 */
        esbuildOptions: {
            plugins: [
                esbuildPluginMonacoEditorNls({
                    locale: Languages.zh_hans,
                }),
            ],
        },
    },
    plugins: [
        reactRefresh(),
        MonacoEditorNlsPlugin({locale: Languages.zh_hans}),
    ],
});
```

Joying it

```shell
npm run example
```


### Using custom locale

> It dependency on [vscode-loc](https://github.com/microsoft/vscode-loc) to get the locales.

- First

```shell
npm create-locale
```

### Question

1. Incomplete localization

> try using custom locale , please