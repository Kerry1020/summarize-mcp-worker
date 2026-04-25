# summarize-mcp-worker

基于 Cloudflare Worker 的 MCP 服务器，提供网页内容提取和轻量级抽取式摘要——无需外部模型依赖。

## MCP 工具

| 工具 | 说明 |
|------|------|
| `fetch_url` | 获取 URL 并返回原始响应元数据和文本预览。 |
| `extract_clean` | 提取网页正文、标题、段落，去除广告和导航。 |
| `summarize` | 从 URL 或文本生成抽取式摘要（基于关键词频率选句），无需 LLM。 |
| `extract_metadata` | 提取页面元数据：标题、描述、作者、语言、发布时间等。 |
| `health` | 健康检查。 |

## 本地开发

```bash
npm install
npx wrangler dev --local --port 8792
```

## 部署

```bash
npx wrangler deploy
```

## 项目结构

```
summarize-mcp-worker/
├── src/index.js
├── wrangler.toml
├── package.json
└── README.md
```
