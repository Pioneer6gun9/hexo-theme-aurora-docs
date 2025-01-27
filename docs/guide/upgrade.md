# Theme upgrade

## v1.x to v2.x Upgrade

Since all the hexo script and generators had being moved to a separate Hexo plugin package ([hexo-plugin-aurora](https://github.com/auroral-ui/hexo-plugin-aurora)). Therefore the way we install `Hexo Aurora Theme` had changed since v2.x.

### Step 1 - Upgrade Hexo and Hexo Plugins

If you are running an older version of Hexo package, make sure you upgrade it to the latest 6.x+.

<CodeGroup>
  <CodeGroupItem title="YARN">

```shell:no-line-numbers
yarn add hexo@latest
```

  </CodeGroupItem>

  <CodeGroupItem title="NPM">

```shell:no-line-numbers
npm install hexo@latest --save
```

  </CodeGroupItem>
</CodeGroup>

If you are also using other hexo-plugins, make sure you also update them to the latest using the above method.

You can simply just add `@latest` behind the package name to get the latest one.

For example: `yarn add hexo-filter-mathjax@latest`

or just use the follow my `package.json`'s dependencies config below (Last updated 26, July 2023):

```json
...

"dependencies": {
  "hexo": "^6.3.0",
  "hexo-filter-mathjax": "^0.9.0",
  "hexo-generator-archive": "^2.0.0",
  "hexo-generator-category": "^2.0.0",
  "hexo-generator-index": "^3.0.0",
  "hexo-generator-tag": "^2.0.0",
  "hexo-plugin-aurora": "^1.2.0",
  "hexo-renderer-ejs": "^2.0.0",
  "hexo-renderer-marked": "^6.1.0",
  "hexo-renderer-stylus": "^3.0.0",
  "hexo-server": "^3.0.0",
  "hexo-theme-aurora": "^2.0.0"
}

...
```

### Step 2 - Install latest Aurora Theme and Plugin

After you have upgrade all your Hexo related packages, now you can install the latest v2.x theme.

You can simply just run the following command.

<CodeGroup>
  <CodeGroupItem title="YARN">

```shell:no-line-numbers
yarn add hexo-theme-aurora@latest hexo-plugin-aurora@latest
```

  </CodeGroupItem>

  <CodeGroupItem title="NPM">

```shell:no-line-numbers
npm install hexo-theme-aurora@latest hexo-plugin-aurora@latest --save
```

  </CodeGroupItem>
</CodeGroup>

### Step 3 - Clean and Re-generate

After install the latest theme, you need to clean up the existing hexo data and regenerate it.

Simply run the below command:

```shell:no-line-numbers
hexo clean && hexo generate
```

That's it for upgrading from 1.x to 2.x, enjoy!
