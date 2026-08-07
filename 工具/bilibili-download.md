# B 站视频下载教程（yt-dlp）

## 前提：安装 yt-dlp

```bash
# macOS（推荐用 Homebrew）
brew install yt-dlp

# 或者用 pip
pip install yt-dlp
```

验证安装：

```bash
yt-dlp --version
```

---

## 基本下载

```bash
yt-dlp "https://www.bilibili.com/video/BVxxxxxxxxxx/"
```

> 默认下载到当前目录，自动选择最高可用画质。

---

## 常见问题：412 错误

直接下载会报 `HTTP Error 412`，需要提供浏览器登录态（Cookie）。

**解决方法 1：用浏览器 Cookie 下载**

```bash
# Chrome
yt-dlp --cookies-from-browser chrome "视频链接"

# Edge
yt-dlp --cookies-from-browser edge "视频链接"

# Firefox
yt-dlp --cookies-from-browser firefox "视频链接"

# Safari
yt-dlp --cookies-from-browser safari "视频链接"
```

> 运行前确保已在对应浏览器中登录 B 站。

**解决方法 2：使用 --cookies（Windows 推荐）**

Windows 上使用 `--cookies-from-browser` 可能遇到权限等问题，推荐改用 `--cookies`：

```bash
yt-dlp --cookies {your-cookie-file-path} "视频链接"
```

> 可使用 Cookie Editor 插件（Chrome）快速获取 cookie，cookie 文件内容仅支持 Netscape 格式。

---

## 查看可用画质

```bash
yt-dlp --cookies-from-browser edge -F "视频链接"
```

输出示例：

```
ID       EXT  RESOLUTION  NOTE
30064    mp4  1920x1080   1080P 高清
100026   mp4  1920x1080   1080P 高帧率
80       mp4  1280x720    720P 高清
...
```

> 4K / 1080P 高码率需要大会员账号。

### 下载指定画质

```bash
yt-dlp --cookies-from-browser edge -f 30064 "视频链接"
```

---

## 下载字幕

### 查看可用字幕

```bash
yt-dlp --cookies-from-browser edge --list-subs "视频链接"
```

常见字幕类型：

| 代码      | 说明             |
| --------- | ---------------- |
| `ai-zh`   | AI 生成中文字幕  |
| `ai-en`   | AI 生成英文字幕  |
| `danmaku` | 弹幕（XML 格式） |

### 仅下载字幕（不下载视频）

```bash
yt-dlp --cookies-from-browser edge --skip-download --write-sub --sub-lang ai-zh "视频链接"
```

### 下载视频 + 字幕

```bash
yt-dlp --cookies-from-browser edge --write-sub --sub-lang ai-zh "视频链接"
```

---

## 指定保存路径和文件名

```bash
# 保存到指定目录
yt-dlp --cookies-from-browser edge -o "~/Downloads/%(title)s.%(ext)s" "视频链接"

# 自定义文件名模板
yt-dlp --cookies-from-browser edge -o "%(upload_date)s_%(title)s.%(ext)s" "视频链接"
```

常用模板变量：

| 变量              | 说明       |
| ----------------- | ---------- |
| `%(title)s`       | 视频标题   |
| `%(id)s`          | BV 号      |
| `%(upload_date)s` | 上传日期   |
| `%(ext)s`         | 文件扩展名 |

---

## 下载合集 / 列表

```bash
# 下载 UP 主的某个合集
yt-dlp --cookies-from-browser edge "合集页面链接"

# 只下载前 5 个
yt-dlp --cookies-from-browser edge --playlist-end 5 "合集链接"

# 下载指定范围（第 3 到第 8 个）
yt-dlp --cookies-from-browser edge --playlist-items 3-8 "合集链接"
```

---

## 常用完整示例

```bash
# 下载 1080P 视频 + 中文字幕，保存到桌面
yt-dlp \
  --cookies-from-browser edge \
  --write-sub \
  --sub-lang ai-zh \
  -o "~/Desktop/%(title)s.%(ext)s" \
  "https://www.bilibili.com/video/BVxxxxxxxxxx/"
```

---

## 更新 yt-dlp

B 站频繁更新反爬策略，建议定期更新工具：

```bash
brew upgrade yt-dlp
# 或
yt-dlp -U
```
