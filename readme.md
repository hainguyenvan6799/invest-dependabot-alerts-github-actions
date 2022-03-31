Instruction use this template
- Go to https://github.dev.cybozu.co.jp/kintone-plugins/development-template -> click Use this template -> create your own repository.

Plugin sample instruction: 

<h2>Requirement</h2>
```
    Node.js
    Git
```

<h2>Private Key</h2>
```
  npm run generate-plugin-private-key
  Output:
    key/private.key 
```

<h2>Eslint</h2>
``` npm run lint ```

<h2>How to build</h2>
```
$ cd /tmp
$ git clone https://github.dev.cybozu.co.jp/kintone-plugins/sample-plugin
$ cd sample-plugin
$ npm i
$ npm run build
```

<h2>Output Files</h2>
``` release/sample-plugin.zip ```

<h2>Supported Web & Mobile</h2>
<ul>
  <li>PC/Mobile: Chrome, Safari</li>
</ul>

<h2>Install Plug-in</h2>

See the following document.
<ul>
  <li>https://help.cybozu.com/en/k/admin/plugin.html (EN)</li>
  <li>https://help.cybozu.com/ja/k/admin/plugin.html (JA)</li>    
</ul>

<h2>Licence</h2>

MIT License

<h2>Copyright</h2>

Copyright(c) Cybozu, Inc.

- After cloned Github template repository for kintone plugin:
I. You need to change the source's name in two places:
1. In package.json
``` 
{
  "name": "@kintone-plugins/{plugin_name}",
  ...
}
```

2. In license_finder/doc/dependency_decisions.yml (apply its own license)

```
...
- - :approve
  - "@kintone-plugins/{plugin_name}"
  - :who: 
    :why: In npm, a check of the License Finder will include the product itself.
    :versions: []
    :when: 2022-03-21 08:14:07.169344000 Z
```
II. Developers can change some plugin's informations:
1. Name (EN, JA, ZH)
  - In manifest.json:
  ```
    {
      ...,
      "name": { 
        "en": "Sample Plug-in",
        "ja": "Sample Plug-in",
        "zh": "Sample Plug-in"
      },
      ...
    }
  ```
2. Description about plugin (EN, JA, ZH)
  - In manifest.json:
  ```
    {
      ...
      "description": { 
        "en": "Sample plug-in description.",
        "ja": "Sample plug-in description.",
        "zh": "Sample plug-in description."
      },
      ...
    }
  ```
3. Icon:
  Save a new icon image to plugin/src/image and define the path in manifest.json:
  ```
    ...,
    "icon": "src/image/icon.png",
    ...
  ```
4. The name of plugin zip file
  Go to webpack.config.js -> pluginZipPath -> enter another name ./release/{another_name}.zip
  ```
  plugins: [
      ...,
      new KintonePlugin({
        manifestJSONPath: "./manifest.json",
        privateKeyPath: "./key/private.ppk",
        pluginZipPath: `./release/github_template_v${version}.zip`,
      }),
  ],
  ```



