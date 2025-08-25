# ComfyUI RSS Feed Reader

一个用于ComfyUI的RSS新闻采集节点，可以从RSS feeds中获取最新新闻内容并格式化输出。

## 功能说明

这个节点可以：
- 从任意RSS feed URL获取最新新闻内容
- 自动解析RSS feed结构
- 提取新闻标题和描述
- 输出格式化的文本内容，可直接用于后续处理

## 安装要求

- Python 3.x
- feedparser库（已在requirements.txt中指定）

安装依赖：
```bash
pip install -r requirements.txt
```

## 节点列表

### RSS Feed Reader

**节点名称**: `RSSFeedNode`  
**显示名称**: `RSS Feed Reader`  
**分类**: `Data Fetching`

#### 输入参数

| 参数名 | 类型 | 必选 | 默认值 | 说明 |
|--------|------|------|---------|------|
| feed_url | STRING | ✅ | http://example.com/rss | RSS feed的完整URL地址 |

**参数详情**:
- `feed_url`: RSS订阅源的URL地址
  - 支持HTTP和HTTPS协议
  - 必须是有效的RSS/XML格式的feed
  - 常见格式如：`https://example.com/feed/`, `https://example.com/rss.xml`

#### 输出

| 输出名 | 类型 | 说明 |
|--------|------|------|
| script_output | STRING | 格式化的新闻内容文本 |

**输出格式**:
```
News Update:
Title: [新闻标题1]
Description: [新闻描述1]

Title: [新闻标题2]
Description: [新闻描述2]

...
```

#### 功能特点

- **自动解析**: 使用feedparser库自动解析各种RSS格式
- **批量获取**: 一次获取feed中的所有可用新闻条目
- **格式化输出**: 统一的文本格式，便于后续处理
- **错误处理**: 自动处理网络错误和解析错误

## 使用示例

### 基本使用

1. 在ComfyUI中添加"RSS Feed Reader"节点
2. 在`feed_url`输入框中输入RSS地址
3. 节点将输出格式化的新闻内容

### 支持的RSS源示例

**新闻媒体**:
```
https://www.bbc.com/news/rss.xml
https://rss.cnn.com/rss/edition.rss
https://feeds.reuters.com/reuters/topNews
```

**科技资讯**:
```
https://feeds.feedburner.com/TechCrunch
https://www.wired.com/feed/rss
https://feeds.arstechnica.com/arstechnica/index
```

**加密货币**:
```
https://www.newsbtc.com/feed/
https://cryptopotato.com/feed/
https://beincrypto.com/feed/
```

### 工作流集成

```
RSS Feed Reader → Text Processing Node → Output Node
```

可以将RSS输出连接到：
- 文本分析节点
- AI对话节点
- 文件保存节点
- 其他文本处理节点

## 技术实现

- **核心库**: feedparser - 强大的RSS/Atom解析库
- **网络请求**: 支持HTTP/HTTPS协议
- **编码处理**: 自动处理各种字符编码
- **容错机制**: 处理无效feed和网络异常

## 常见问题

**Q: 节点无法获取内容？**
A: 请检查：
- RSS URL是否正确且可访问
- 网络连接是否正常
- RSS源是否支持CORS（如果在浏览器环境中）

**Q: 输出内容乱码？**
A: feedparser会自动处理大多数编码问题，如果仍有问题，请检查RSS源的编码格式。

**Q: 获取的新闻数量？**
A: 取决于RSS源提供的条目数量，通常为最新的10-20条新闻。

## 许可证

本项目基于 Creative Commons Attribution-NonCommercial 4.0 International License 许可 - 详见 [LICENSE](Licence.txt) 文件。

## 版本信息

- 当前版本：基于ComfyUI节点标准开发
- 依赖：feedparser库
- 兼容性：ComfyUI最新版本

## 贡献

欢迎提交Issue和Pull Request来改进这个节点！