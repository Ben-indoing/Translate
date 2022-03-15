## 1.1.5

- Fix issues when canceling a saving process. (Windows / Linux)
- 修复取消保存时的问题
- Improve undo when auto save is enabled. (Windows / Linux)
- 改进撤销功能，当自动保存时
- Fix image with absolute path not shown in exported PDF. (macOS)
- 修复从PDF导出绝对路径的图片不能显示的问题

## 1.1.4

- Fix display issue under languages including Indonesian, French, Catalan and Traditional Chinese.
- 修复印尼语，法语，加泰罗尼亚语和繁体中文显示问题

## 1.1.3

#### Fix

- Fix a critical issue that some file cannot be opened.
- 修复一个一些文件不能被打开的关键问题
- Fix settings for epub cannot be shown in preferences panel.
- 修复epub的设置不能在偏好版面显示的问题

## 1.1.2

See [detail](https://support.typora.io/What's-New-1.1/).

#### New / Improvements

- Add Malay language support.
- Add Slovenian language support.
- Fix typo and update translations in other languages.
- 修复排版和升级在翻译
- Allow create file when open non-exist file via command line.
- 当打开不存在的文件时， 允许通过命令行创建文见
- Allow create file when open target link that does not have existing file.
- 当打开链接并不存在文件时， 允许创建文件
- Allow open other files' anchor position directly via file link.
- 允许通过文件链接打开其作者位置
- More compact context menu under Windows / Linux.
- 更多紧凑的上下文菜单
- Support copy / cut while line when nothing is selected.
- 允许复制剪切行，当没有东西被选中时
- Add option to disable or enable physics package.
- 增加选项禁用或启用的物理包
- Allow pasting markdown with Command-Option-Shift-V on macOS.
- Support offline activation and provide web UI to manage used license code.
- 支持离线激活，并且提供网络界面来管理证书码
- Sign Windows executables and installers.
- 为windows的可执行程序和安装程序签名
- Support default / theme font size for exported image.
- 对导出的图片支持默认主题字体大小
- Ensure downloaded image has image file extension.
- 确保下载的图片有图像文件扩展名
- Support loading local image files with user append hashes.
- 支持导入本地图片文件附加用户散列

#### Fix

- Fix security issue which may cause XSS.
- 解决可能由跨站点脚本攻击引起的安全问题
- Fix custom font size for exported image.
- 修复导出图片的自定义字体大小问题
- Fix multiple BOM be added when saving files with BOM header.
- 修复用字节头保存文件时增加多个字节顺序标记的问题
- Fix copy as MathML not working for math block.
- 修复数学模块复制MathMl不起作用的bug
- Fix math auto numbering get wrongly numbered labels.
- 修复数学自动计数获得错误的标签数
- Fix file tree UI under smaller customer font size.
- 修复文件树用户界面自定义字体大小变小的问题
- Fix always on top cannot be turned off under macOS.
- Fix image corrupted if your Typora is zoomed.

## 1.0.3

\1. Add option to allow connect to activation server in China.

[Windows (64bit)EXE](https://download.typora.io/windows/typora-setup-x64-1.0.3.exe) [Windows (32bit)EXE](https://download.typora.io/windows/typora-setup-ia32-1.0.3.exe) [Windows (ARM)EXE](https://download.typora.io/windows/typora-setup-arm64-1.0.3.exe)
[Linux (64bit)DEB](https://download.typora.io/linux/typora_1.0.3_amd64.deb) [Linux (64bit)TAR](https://download.typora.io/linux/Typora-linux-x64-1.0.3.tar.gz) [Linux (ARM)DEB](https://download.typora.io/linux/typora_1.0.3_arm64.deb) [Linux (ARM)TAR](https://download.typora.io/linux/Typora-linux-arm64-1.0.3.tar.gz)

## 1.0.2

\1. Fix activation process on some older macOS version.

\2. Fix indent on lists.

## 1.0.0

Typora finally reaches v1.0 🎉🎉🎉🎉

(A **license code** is required after this upgrade.)

Thank you all beta users who helped make Typora better.

[macOSDMG](https://download.typora.io/mac/Typora-1.0.5.dmg) [Windows (64bit)EXE](https://download.typora.io/windows/typora-setup-x64-1.0.3.exe) [Windows (32bit)EXE](https://download.typora.io/windows/typora-setup-ia32-1.0.3.exe) [Windows (ARM)EXE](https://download.typora.io/windows/typora-setup-arm64-3.exe)
[Linux (64bit)DEB](https://download.typora.io/linux/typora_1.0.3_amd64.deb) [Linux (64bit)TAR](https://download.typora.io/linux/Typora-linux-x64-1.0.3.tar.gz) [Linux (ARM)DEB](https://download.typora.io/linux/typora_1.0.3_arm64.deb) [Linux (ARM)TAR](https://download.typora.io/linux/Typora-linux-arm64-1.0.3.tar.gz)

(compared to first beta)

- Support YAML front matters (0.8.5), LaTeX math (0.8.7), `[toc]` (0.9.2), many new code syntax highlights, subscript and superscript (0.9.6), underline (0.9.7), highlight (0.9.8.7), diagrams (0.9.9.7) , local file link (0.9.9.8.2), table editing (0.9.9.8.8), HTML (0.9.9.17), etc...
- Improve editing user experience, support auto pair (0.9.8.7), smart punctuation (0.9.9.16).
- Launched [Theme Gallery](https://theme.typora.io/) (0.9.9.7.8) and [Support Website](https://support.typora.io/).
- Provide outline view (0.9.2), word count (0.9.5), focus mode and typewriter mode (0.9.9.6), dark themes (0.9.9.9.2).
- Provide Typora in other languages (start from 0.9.9.11.2) and spellcheck support.
- File management, including "Open Quickly" (0.9.9.0), file tree / list (0.9.9.10), options when launch (0.9.9.15), global search (0.9.9.20), etc.
- Better image management, include supporting relative path (0.9.4), image copy-to (0.9.9.18) and upload operations (0.9.9.32).
- More advanced export functions (0.10.6).
- New design of preferences panel(0.9.9.27), new icon (0.10.6), and many new themes.
- And much more...

Read More in https://support.typora.io/What's-New-1.0

[Purchase Now](https://store.typora.io/)



## 1.2.0-dev

[macOSDMG](https://download.typora.io/mac/Typora-1.2.0-dev.dmg)

- Improve performance when editing file with many large images on macOS.

## 1.1.1-dev

[macOSDMG](https://download.typora.io/mac/Typora-1.1.1-dev.dmg) [Windows (64bit)EXE](https://download.typora.io/windows/typora-setup-x64-1.1.1-dev.exe)

- Improve delete current block and delete current line.
- Update i18n translations.
- Fix title bar display for auto save.
- Other bug fix.

## 1.1.0-dev

[macOSDMG](https://download.typora.io/mac/Typora-1.1.0-dev.dmg) [Windows (64bit)EXE](https://download.typora.io/windows/typora-setup-x64-1.1.0-dev.exe)

See [detail](https://support.typora.io/What's-New-1.1/).

#### New / Improvements

- Add Malay language support.
- Add Slovenian language support.
- Fix typo and update translations in other languages.
- Allow create file when open non-exist file via command line.
- Allow create file when open target link that does not have existing file.
- Allow open other files' anchor position directly via file link.
- More compact context menu under Windows / Linux.
- Support copy / cut while line when nothing is selected.
- Add option to disable or enable physics package.
- Allow pasting markdown with Command-Option-Shift-V on macOS.
- Support offline activation and provide web UI to manage used license code.
- Sign Windows executables and installers.
- Support default / theme font size for exported image.
- Ensure downloaded image has image file extension.
- Support loading local image files with user append hashes.

#### Fix

- Fix security issue which may cause XSS.
- Fix custom font size for exported image.
- Fix multiple BOM be added when saving files with BOM header.
- Fix copy as MathML not working for math block.
- Fix math auto numbering get wrongly numbered labels.
- Fix file tree UI under smaller customer font size.
- Fix always on top cannot be turned off under macOS.
- Fix image corrupted if your Typora is zoomed.

## 1.0.0

[macOSDMG](https://download.typora.io/mac/Typora-1.0.5.dmg) [Windows (64bit)EXE](https://download.typora.io/windows/typora-setup-x64-1.0.3.exe) [Windows (32bit)EXE](https://download.typora.io/windows/typora-setup-ia32-1.0.3.exe) [Windows (ARM)EXE](https://download.typora.io/windows/typora-setup-arm64-1.0.2.exe)
[Linux (64bit)DEB](https://download.typora.io/linux/typora_1.0.3_amd64.deb) [Linux (64bit)TAR](https://download.typora.io/linux/Typora-linux-x64-1.0.3.tar.gz) [Linux (ARM)DEB](https://download.typora.io/linux/typora_1.0.3_arm64.deb) [Linux (ARM)TAR](https://download.typora.io/linux/Typora-linux-arm64-1.0.3.tar.gz)

Typora finally reaches v1.0 🎉🎉🎉🎉

Read More in [What's New](https://support.typora.io/What's-New-1.0)

[Purchase Now](https://store.typora.io/)

 

 

 

------

### Old Beta

#### 0.11.18

\1. Add warnings when user try to edit file from backup location.

\2. Line break should be rendered as whitespace when ignore line break is enabled.

\3. Fix new file in tile tree will result to duplicate files.

\4. Fix bug that table with tabs cannot be correct parsed.

\5. Fix inline math preview issue.

\6. Fix bug that users cannot jump from some internal links.

\7. Fix some cursor issue.

\8. Fix some copy related menu get disabled when selecting multiple blocks.

 

### More Beta

[old macOS beta](https://typora.io/dev_release.html)

[old Windows / Linux beta](https://typora.io/windows/dev_release.html)