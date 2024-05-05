# SvgIcon

SvgIcon 是一个用于封装 svg 图像文件的 Vue3 组件。该组件旨在让你能够在 Vue3 项目中快速、方便、灵活的使用各种 svg 图像。

使用该组件，可以方便灵活地对 svg 图像进行各种控制，如指定图像，修改大小及颜色、透明度等。

## 安装

使用以下命令即可安装该组件：

```sh
#npm
npm i @mopsite/svg-icon

#pnpm
pnpm add @mopsite/svg-icon

#bun
bun add @mopsite/svg-icon
```

## 引入

安装完成之后，你可以在 Vue3 项目的 `src/main.js` 文件中以下面的方式引入：

```js
import svgIcon from '@mopsite/svg-icon'
```

然后，像使用插件一样使用它：

```js
createApp(App).use(svgIcon).mount('#app')
```

这样，你就成功的在你的项目中全局注册了一个 SvgIcon 组件。

## 使用

该组件使用 `<SvgIcon />` 单标签样式即可。

如果不给该组件传递任何属性，它将显示为默认的 svg 图像及样式。

你还可以给该组件传递一些属性，以对其进行控制：

- url

  `url` 属性为字符串，表示需要使用的 svg 图像的地址。可以是本地地址，也可以是网络地址。

  如果使用本地 svg 文件，需要安装 [vite-svg-loader](https://github.com/jpkleemans/vite-svg-loader) 插件（网络 svg 文件不需要安装）：

  ```sh
  #npm
  npm install vite-svg-loader -D

  #pnpm
  pnpm add vite-svg-loader -D

  #bun
  bun add vite-svg-loader -D
  ```

  然后在 `vite.config.js` 文件中导入并使用它即可：

  ```js
  import svgLoader from 'vite-svg-loader'

  export default defineConfig({
    plugins: [vue(), svgLoader()]
  })
  ```

  **需要注意的是，地址不包含 svg 文件名，并且必须以 `/` 结尾**。

  `<SvgIcon url="/src/assets/svgs/" />`

  或

  `<SvgIcon url="https://xxx.com/svgs/" />`

- name

  `name` 属性为字符串，用于指定 svg 文件的文件名（不包含后缀名 `.svg`）。

  如 `<SvgIcon url="/src/assets/svgs/" name="logo" />`，这将会自动拼接成 svg 文件的完整地址 `/src/assets/svgs/logo.svg`。

- size

  `size` 属性为字符串，用于指定 svg 文件的显示大小。该值应为任意的 CSS 大小值，默认为 `1em`。其本质是同时将 svg 图像的 `width` 和 `height` 属性设置为 `size` 值。

  `<SvgIcon size="3em" />` 或 `<SvgIcon size="28px" />` 等值都适用。

- color

  `color` 属性可以是字符串也可以是对象，用于指定 svg 图像的显示颜色。

  如果该值是字符串时，应为任意的 CSS 颜色值，默认为 `currentColor`。

  `<SvgIcon color="red" />` 或 `<SvgIcon color="#f00" />` 等值都适用。

  当你使用类似 Font Awesome 的双色图标时，可以使用 `color` 属性的对象形式。该对象包含 `primary` 和 `secondary` 两个属性，用于分别设置主色和次色的颜色。

- opacity

  `opacity` 属性可以是 0~1 的数字，也可以是对象。该属性用于设置 svg 图像的透明度，其用法与 `color` 属性基本一致。
