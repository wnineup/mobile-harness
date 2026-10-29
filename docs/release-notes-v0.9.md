手机本地优先的 AI Agent 客户端 · 首个公开预览版

---

## 下载

`mobile-harness-0.9.0-preview.apk`　4.4 MB

```text
SHA256  F868E91A7F0F9BCE6C2693D85EDEDA9F0D574C12529C21EB69E75A464019D0AD
```

要求 Android 10（API 29）及以上。**预览版使用 debug 签名**：将来换成正式签名时，必须先卸载旧版再装，否则会提示签名冲突。

## 5 分钟验证

1. 侧载 APK（需允许"安装未知应用"）
2. 打开应用 → 右上角设置 → 填自己的 DeepSeek API Key（应用不含 Key）→ 保存 → 测试连接
3. 新建对话，输入：`读一下 notes/today.md，告诉我里面有什么`
4. 看到工具调用卡片 `read_text({"path":"notes/today.md"})`，回复基于文件真实内容，就算跑通

## 这一版有什么

- **手机本地 agent 循环**：流式对话 → 调工具 → 读写文件 → 结果回灌，单轮最多 24 步
- **工具**：`list_dir` / `read_text` / `write_text` / `search_text` / `delete_path` / `fetch_url` / `web_search` / `open_url`，另支持系统文件选择器授权的目录（SAF）
- **文件工作区**：浏览、新建、重命名、删除、编辑、预览；接收其他应用分享的文本与文件
- **对话**：SSE 流式、停止、错误分类（401/402/429/5xx）、Markdown 与表格渲染、图片直传与多图
- **安全**：API Key 存本机 Keystore；Agent 权限三档（只读 / 每次询问 / 完全权限）；工具调用记录落库可回看
- 安装包经 R8 + 资源裁剪，4.4 MB

## 已验证

- Redmi K90（Android 16）、OPPO A6s Pro 5G（Android 16）
- 27 个单元测试通过

## 已知限制

- 需要自备 API Key，无账号体系
- 未做多机型兼容性测试；低版本系统、其他品牌请自担风险
- 未上架任何应用商店；debug 签名
- 未实现：PDF / Office / EPUB 解析、多端同步、云端中继、多人协作、自动清理、语音
- "全部文件访问"默认关闭，需要读写 `/sdcard/...` 时得在设置里手动打开

## 反馈

装了之后跑不通、崩了、或者哪一步看不懂，直接把机型 + 安卓版本 + 复现步骤发我，比截图更有用。
