# WeChat Batch Clipper

批量从 CSV/TXT 文件中提取网页（特别是微信文章）内容，利用 `obsidian-clipper` CLI 将其抓取为结构化 Markdown 文件并保存到指定目录。

## 触发条件

当用户提及以下内容时触发：
- 批量提取微信文章/网页内容
- 批量保存网页为 Markdown
- 批量抓取网页/链接
- 将表格中的网址批量提取保存
- obsidian web clipper 批量操作
- 批量保存文章到本地/Obsidian

## Workflow

### 前置检查

1. 确认 Node.js 已安装：运行 `node --version`
2. 确认 `obsidian-clipper` CLI 已全局安装：运行 `obsidian-clipper --version`
   - 如未安装，运行 `npm install -g obsidian-clipper`
3. 确认用户已准备好包含 URL 的 CSV 文件

### CSV 文件格式

CSV 文件应包含至少一列 URL：

**格式一：仅 URL 列（自动从 URL 生成文件名）**
```csv
URL
https://mp.weixin.qq.com/s/xxxxx
https://mp.weixin.qq.com/s/yyyyy
```

**格式二：URL + 文件名/标题列**
```csv
URL,Title
https://mp.weixin.qq.com/s/xxxxx,人工智能新趋势
https://mp.weixin.qq.com/s/yyyyy,区块链技术解析
```

### 执行步骤

1. 询问/确认用户以下信息：
   - CSV 文件路径
   - 保存输出的目录路径（默认为 `~/Clippings/`）

2. 使用本 skill 目录下的 `scripts/batch_clipper.js` 脚本执行批量抓取：
   ```bash
   node <skill_dir>/scripts/batch_clipper.js \
     --csv /path/to/links.csv \
     --output /path/to/output/dir \
     --concurrency 3
   ```

3. 参数说明：
   - `--csv`: CSV 文件路径（必填）
   - `--output`: 输出目录路径（必填）
   - `--concurrency`: 并发抓取数量（默认 3，建议不超过 5）
   - `--retry`: 失败重试次数（默认 0）

4. 报告执行结果：成功数量、失败数量、失败的具体 URL

## 注意事项

- 微信文章可能需要特殊处理（如登录状态），如果抓取失败需提示用户
- 建议并发数不超过 3-5，避免被封 IP
- 微信文章 URL 有效期可能较短，建议尽快抓取
- 如果 obsidian-clipper 无法抓取微信文章，可以考虑使用 puppeteer 或 Playwright 等替代方案
