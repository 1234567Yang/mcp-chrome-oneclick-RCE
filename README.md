# mcp-chrome-oneclick-RCE
PoC for https://github.com/hangwin/mcp-chrome

用户点击链接，即可实现主机远程代码执行，Chrome / Firefox 等有 Defense-in-depth，但是微信浏览器点击就中招。

# 请作者看到后立马添加补丁，如有必要我可以提供任何帮助！建议修复：
* 立刻修复 parser differential CORS 问题
* 为 MCP 服务器添加并开启 `X-Authorization` 功能
* 针对侧边聊天栏，添加并开启 `X-Authorization` 功能
* 针对侧边聊天栏，禁用 Claude 的代码执行

# 用户建议：
## 最安全：卸载和此扩展相关的 Node.js mcp-chrome-bridge 等桥接库，禁用此 Chrome 扩展，直到代码被修复
## 其次：禁用此 Chrome 扩展

通用提醒：互联网大逃杀时代，不要点击来路不明的链接。
