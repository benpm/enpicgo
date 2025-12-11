_THIS IS A FORK!_

<div align="center">
  <img src="https://raw.githubusercontent.com/Molunerfinn/test/master/picgo/New%20LOGO-150.png" alt="">
  <h1>PicGo</h1>
  <blockquote>A new experience for image uploading and management</blockquote>
  <a href="https://github.com/Molunerfinn/PicGo/actions">
    <img src="https://img.shields.io/badge/code%20style-standard-green.svg?style=flat-square" alt="">
  </a>
  <a href="https://github.com/Molunerfinn/PicGo/actions">
    <img src="https://github.com/Molunerfinn/PicGo/actions/workflows/main.yml/badge.svg" alt="">
  </a>
  <a href="https://github.com/Molunerfinn/PicGo/releases">
    <img src="https://img.shields.io/github/downloads/Molunerfinn/PicGo/total.svg?style=flat-square" alt="">
  </a>
  <a href="https://github.com/Molunerfinn/PicGo/releases/latest">
    <img src="https://img.shields.io/github/release/Molunerfinn/PicGo.svg?style=flat-square" alt="">
  </a>
  <a href="https://github.com/PicGo/bump-version">
    <img src="https://img.shields.io/badge/picgo-convention-blue.svg?style=flat-square" alt="">
  </a>
</div>

## Application Overview

**PicGo: A tool for quickly uploading images and getting image URL links**

PicGo natively supports the following image hosting services:

- `Qiniu` v1.0
- `Tencent Cloud COS v4\v5` v1.1 & v1.5.0
- `Upyun` v1.2.0
- `GitHub` v1.5.0
- `SM.MS V2` v2.3.0-beta.0
- `Alibaba Cloud OSS` v1.6.0
- `Imgur` v1.6.0

**The core application will no longer add support for additional default image hosting services. You can develop third-party image hosting plugins yourself. See [PicGo-Core](https://picgo.github.io/PicGo-Core-Doc/) for details**.

## Key Features

- Support for drag and drop image uploads
- Support for uploading the first image in clipboard via hotkey
- Windows and macOS support for right-clicking image files to upload via context menu (v2.1.0+)
- Automatically copy link to clipboard after uploading images
- Support for custom link format copied to clipboard
- Support for customizable hotkeys, default quick upload hotkey: `command+shift+p` (macOS) | `control+shift+p` (Windows\Linux)
- Support for plugin system, existing plugins support Gitee, QingCloud and other third-party image hosting services
  - More third-party plugins and applications built on PicGo can be found at [Awesome-PicGo](https://github.com/PicGo/Awesome-PicGo). Contributions are welcome!
- Support for uploading via HTTP requests to PicGo (v2.2.0+)
- More features for you to discover, and new features are continuously being developed
  - Development progress can be viewed at [Projects](https://github.com/Molunerfinn/PicGo/projects), which is synchronized with development updates
  <!-- - Welcome to join the [official discussion forum](https://github.com/Molunerfinn/PicGo/discussions) to communicate with me -->

**If this is your first time using PicGo, please refer to the [User Documentation](https://picgo.github.io/PicGo-Doc/guide/getting-started.html). If you encounter problems, you can also check the [FAQ](https://github.com/Molunerfinn/PicGo/blob/dev/FAQ.md) and closed [issues](https://github.com/Molunerfinn/PicGo/issues?q=is%3Aissue+is%3Aclosed).**

## Download and Installation

| Download Source                               | Address/Installation Method                                 | Platform   | Notes                                                                          |
| --------------------------------------------- | ----------------------------------------------------------- | ---------- | ------------------------------------------------------------------------------ |
| GitHub Release                                | https://github.com/Molunerfinn/PicGo/releases               | All        | Download speed may be slow in China                                            |
| [SDU Mirror](https://mirrors.sdu.edu.cn/)     | https://mirrors.sdu.edu.cn/github-release/Molunerfinn_PicGo | All        | Thanks to [Shandong University Mirror](https://mirrors.sdu.edu.cn/) for mirror support |
| [Scoop](https://scoop.sh/)                    | `scoop bucket add extras` & `scoop install picgo`           | Windows    | Thanks to @huangnauh and @Gladtbam for contributions                           |
| [Chocolatey](https://chocolatey.org/)         | `choco install picgo`                                       | Windows    | Thanks to @iYato for contributions                                             |
| [Homebrew](https://brew.sh/)                  | `brew install picgo --cask`                                 | macOS      | Thanks to @womeimingzi11 for contributions                                     |
| [AUR](https://aur.archlinux.org/packages/yay) | `yay -S picgo-appimage`                                     | Arch-Linux | Thanks to @houbaron for contributions                                          |

## Application Screenshots

![](https://raw.githubusercontent.com/Molunerfinn/test/master/picgo/picgo-2.0.gif)

![picgo-menubar](https://user-images.githubusercontent.com/12621342/34242310-b5056510-e655-11e7-8568-60ffd4f71910.gif)

## Development Guide

> Currently only tested on Mac and Windows. Linux platform has not been tested.

If you want to learn, develop, modify, or build PicGo yourself, you can follow the instructions below:

> If you want to learn Electron-vue development, you can check out my tutorial series - [Electron-vue Development Practice](https://molunerfinn.com/tags/Electron-vue/)

1. You need to have Node and Git environment, and understand npm-related knowledge.
2. `git clone https://github.com/Molunerfinn/PicGo.git` and enter the project.
3. `yarn` to download dependencies. Note that if you don't have `yarn`, please go to the [official website](https://classic.yarnpkg.com/en/docs/install) to download and install it before use. **Using `npm install` will cause unknown errors!**
4. Mac requires Xcode environment, Windows requires VS environment.
5. If you need to contribute code, please refer to the [Contribution Guide](./CONTRIBUTING.md).

### Development Mode

Enter `npm run electron:serve` to enter development mode, which has hot reload features. However, please note that development mode is unstable and may have process crashes. In this case, you need to:

```bash
ctrl+c # Exit development mode
npm run dev # Re-enter development mode
```

**Note: After running Windows development mode, the PicGo application icon will appear in the application area in the lower right corner of the bottom taskbar.**

### Production Mode

If you need to build it yourself, you can run `npm run build` to start building. After a successful build, the corresponding installation files will appear in the `dist` directory.

**Note**: If your network environment is not good, `electron-builder` may fail to download the `electron` binary file. In this case, you need to specify the `electron` source as a mirror before building:

```bash
export ELECTRON_MIRROR="https://npmmirror.com/mirrors/electron/"
# On Windows, you can use set ELECTRON_MIRROR=https://npmmirror.com/mirrors/electron/ (no quotes needed)
npm run build
```

You only need to specify the mirror source for the first build. Subsequent builds do not need to be specified. Binary files are downloaded in the `~/.electron/` directory. If you want to update the `electron` build version, you can delete the `~/.electron/` directory, and then re-run the previous step to let `electron-builder` download the latest `electron` binary file.

## Related Projects

- [vs-picgo](https://github.com/PicGo/vs-picgo): PicGo VS Code version.
- [flutter-picgo](https://github.com/PicGo/flutter-picgo): PicGo mobile app (supports Android and iOS).
- [PicHoro](https://github.com/Kuingsmile/PicHoro): Another mobile app that supports PicGo configuration (currently only supports Android).

## Sponsorship

If you like PicGo and it has been helpful to you, feel free to buy me a cup of coffee~

Alipay:

![](https://user-images.githubusercontent.com/12621342/34188165-e7cdf372-e56f-11e7-8732-1338c88b9bb7.jpg)

WeChat Pay:

![](https://user-images.githubusercontent.com/12621342/34188201-212cda84-e570-11e7-9b7a-abb298699d85.jpg)

## License

[MIT](http://opensource.org/licenses/MIT)

Copyright (c) 2017 - Now Molunerfinn
