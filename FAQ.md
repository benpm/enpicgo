## Frequently Asked Questions

> During the use of PicGo, you will encounter many issues, but many of these issues have been asked and resolved before. So you can first check the [User Documentation](https://picgo.github.io/PicGo-Doc/guide/getting-started.html#%E5%BF%AB%E9%80%9F%E4%B8%8A%E6%89%8B), this FAQ, and those closed [issues](https://github.com/Molunerfinn/PicGo/issues?q=is%3Aissue+is%3Aclosed), which should help you find the answer.

## 1. After successfully uploading images to Qiniu, the gallery cannot display them or images are missing the `http://` prefix

This is usually because the `Access URL` in your Qiniu configuration does not have the `http://` or `https://` prefix.

Reference: [issue#79](https://github.com/Molunerfinn/PicGo/issues/79)

## 2. Can remote deletion on image hosting be supported?

No. Some image hosting services (such as Weibo, SM.MS, Imgur, etc.) do not support backend management, so remote deletion is not supported for architectural consistency.

## 3. Can video file uploads be supported?

Currently not. If someone develops a corresponding plugin, it can theoretically support uploading any file type.

## 4. Weibo image hosting cannot display preview images after uploading

This is usually caused by having a global proxy enabled.

Reference: [issue36](https://github.com/Molunerfinn/PicGo/issues/36)

## 5. Can a certain image hosting service be supported?

As of v1.6, PicGo supports the following image hosting services:

- `Weibo` v1.0
- `Qiniu` v1.0
- `Tencent Cloud COS v4\v5` v1.1 & v1.5.0
- `Upyun` v1.2.0
- `GitHub` v1.5.0
- `SM.MS` v1.5.1
- `Alibaba Cloud OSS` v1.6.0
- `Imgur` v1.6.0

Therefore, the core application will no longer support other image hosting services. If you need support for other image hosting services, please refer to existing third-party [plugins](https://github.com/PicGo/Awesome-PicGo). If there is still no image hosting service you need, you are welcome to develop a plugin for everyone to use.

## 6. Setting multiple configurations for one image hosting service

Not possible. Because the current architecture only supports one configuration per image hosting service.

## 7. GitHub image hosting sometimes succeeds and sometimes fails to upload

1. GitHub image hosting does not support uploading files with the same name. If you upload a file with the same name, an error will be reported. It is recommended to enable `Timestamp Rename` to avoid duplicate file names.
2. Issues with GitHub servers and the GFW in China will cause uploads to sometimes succeed and sometimes fail. There is no solution. For stability, please use paid cloud storage such as Alibaba Cloud, Tencent Cloud, etc., which are also not expensive.

## 8. Cannot open the main window of PicGo on Mac

PicGo is a menu bar application on Mac and will not have an icon in the dock. To open the main window, right-click or two-finger tap the PicGo icon in the menu bar and select "Open Detail Window" to open the main window.

## 9. Upload failed or server error

1. The image hosting services that come with PicGo have all been tested. Upload errors are generally not caused by PicGo itself. If you are using GitHub image hosting, please refer to point 7 above.
2. Check PicGo's logs (error logs can be found in PicGo Settings -> Log File Settings -> Click to Open) and see what key information is in the `[PicGo Error]` error message
   1. First search for the error message yourself. You can often find the cause of the problem through Baidu or Google, so you don't need to open an issue.
   2. If there are status codes like `401`, `403`, or other `40X` codes, there is no doubt that your configuration is wrong. Carefully check your configuration to see if there are extra spaces or similar issues.
   3. If there are words like `HttpError`, `RequestError`, or `socket hang up`, it indicates a network problem. I cannot help you solve network problems. Please check your own network, whether there is a proxy, whether DNS settings are normal, etc.
3. Upload failures caused by network problems are usually due to improper proxy settings. If system proxy is enabled, it is recommended to also set the corresponding HTTP proxy in PicGo's proxy settings. Reference [#912](https://github.com/Molunerfinn/PicGo/issues/912)

## 10. No main interface after installing the macOS version

Please find the PicGo icon in the menu bar, then right-click (two-finger tap on trackpad, or mouse right-click), and you can find the "Open Detail Window" menu.

## 11. Gallery suddenly cannot display images OR gallery does not update after uploading OR using Typora+PicGo to upload images successfully but not writing back to Typora

This may be caused by corrupted gallery storage files. You can find the `picgo.db` file in the PicGo configuration file path, delete it (it is recommended to back it up before deleting), and then restart PicGo to try.
Also check the log file for any errors, and you can open an issue if necessary. Versions 2.3.0 and above have resolved the above issues caused by damaged `picgo.db`, so it is recommended to update the version.

## 12. Gitee-related issues

If you encounter upload problems when using Gitee image hosting, since PicGo does not officially provide Gitee upload service, I cannot help you solve it. Please go to the Gitee plugin repository you are using to open related issues.

## 13. After installing PicGo on macOS, it shows "File is damaged" or there is no response after installation

Because PicGo is not signed, it will be blocked by macOS security checks.

1. If you encounter the "File is damaged" situation after installation, please operate as follows:

Trust the developer, which will require you to enter your password:

```
sudo spctl --master-disable
```

Then allow PicGo:

```
xattr -cr /Applications/PicGo.app
```

Then it can be opened normally.

If the following prompt appears

```sh
option -r not recognized

usage: xattr [-slz] file [file ...]
       xattr -p [-slz] attr_name file [file ...]
       xattr -w [-sz] attr_name attr_value file [file ...]
       xattr -d [-s] attr_name file [file ...]
       xattr -c [-s] file [file ...]

The first form lists the names of all xattrs on the given file(s).
The second form (-p) prints the value of the xattr attr_name.
The third form (-w) sets the value of the xattr attr_name to attr_value.
The fourth form (-d) deletes the xattr attr_name.
The fifth form (-c) deletes (clears) all xattrs.

options:
  -h: print this help
  -s: act on symbolic links themselves rather than their targets
  -l: print long format (attr_name: attr_value)
  -z: compress or decompress (if compressed) attribute value in zip format
```
Execute the command

```
xattr -c /Applications/PicGo.app/*
```

If the above command still has no effect, you can try the following command:

```
sudo xattr -d com.apple.quarantine /Applications/PicGo.app/
```

2. If there is no response after installation and opening, please troubleshoot in the following order:
   1. After installing macOS, PicGo will not pop up the main window, because PicGo is designed as a menu bar application in macOS. Pay attention to the icon in your menu bar. If there is a PicGo icon, it means the installation is successful. Click the icon to open the menu bar window. Refer to [point 8 above](#8-cannot-open-the-main-window-of-picgo-on-mac).
   2. If you are on an M1 system and previously installed the x64 version of PicGo, but later updated to the arm64 version and found no response after opening, please restart your computer.
