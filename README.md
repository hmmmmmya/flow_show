# flow_show

## 简介

下面是一个简单的 HTML 和 JavaScript 实现的网页，用于展示一组文本数据的无序动态流动效果。它会随机排列数据，并以动画的形式展示出来。

### 代码说明

1. **HTML 结构**：整个页面主要由一个`container`容器来展示文本数据。
2. **CSS 样式**：页面居中，`container`容器中设置为`position: relative`，每个文本项为`position: absolute`，以便可以任意放置。
3. **JavaScript 逻辑**：
   - `texts`数组保存要展示的文本数据。
   - `getRandomPosition`函数生成随机位置，确保文本显示在容器范围内。
   - `getRandomColor`函数生成随机颜色，为文本提供多彩效果。
   - `displayTexts`函数是核心逻辑：每隔 5 秒清空容器并重新随机排列文本。通过`opacity`和`transition`实现淡入淡出的效果。
4. **定时刷新**：使用`setInterval(displayTexts, 5000)`实现动态刷新，每 5 秒重新生成随机布局。

### 效果

每次刷新时，文本将会以不同的顺序和位置显示，并带有随机颜色，形成动态流动的效果。

## 如何展示为网页

要将上面的代码展示为网页，你可以按照以下步骤操作：

因为浏览器的跨域资源共享（CORS）限制。浏览器限制直接从 `file://` 协议访问本地文件，因此 `fetch` 无法从本地文件系统加载 `data.json`。

### 方法 1：使用本地 HTTP 服务器运行项目

如前面提到的，您可以通过本地服务器来绕过这些限制。这是最推荐的做法。

1. **使用 Python**（在 HTML 和 JSON 文件所在目录下运行以下命令）：

   - 对于 Python 3：

     ```bash
     python -m http.server 8000
     ```

   - 对于 Python 2：

     ```bash
     python -m SimpleHTTPServer 8000
     ```

   然后在浏览器中访问 `http://localhost:8000/index.html`，这样就可以正常加载 `data.json`。

2. **使用 VS Code 的 Live Server 插件**
   - 如果您使用的是 Visual Studio Code，可以安装 **Live Server** 插件。
   - 打开 `index.html` 文件，右键选择“Open with Live Server”，这将自动启动本地服务器并打开浏览器访问页面。

### 方法 2：修改浏览器启动参数（仅用于测试，不推荐在生产环境中使用）

在开发阶段可以绕过 CORS 检查，但这仅用于本地调试，不推荐用于正式环境。

- 在 Windows 上，可以通过以下方式打开 Chrome 并禁用 CORS 检查：

  1. 关闭所有 Chrome 窗口。
  2. 打开命令提示符（CMD）。
  3. 运行以下命令（假设 Chrome 安装在默认路径）：

     ```bash
     "C:\Program Files\Google\Chrome\Application\chrome.exe" --disable-web-security --user-data-dir="C:\chrome_dev"
     ```

  4. 用此窗口打开 `index.html`。

这样 Chrome 会在无 CORS 限制的模式下运行，但请注意关闭它后，再正常启动浏览器时将恢复安全设置。

最好的方法是使用 **方法 1**，通过本地 HTTP 服务器来加载页面和数据文件。这样可以避免 CORS 问题，同时符合正式开发和生产环境的最佳实践。

### 方法 3：部署到 GitHub Pages

1. 创建一个 GitHub 仓库，将`index.html`上传到仓库的根目录。
2. 在 GitHub 仓库页面，打开**Settings**，找到**GitHub Pages**设置，选择`main`分支并保存。
3. GitHub 会提供一个链接，稍等几分钟后访问该链接，就可以看到部署好的网页。
