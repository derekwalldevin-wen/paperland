# 纸境 · 剪纸层叠海报工坊

纯浏览器的照片风格化实验。上传 JPG/PNG，将照片的明暗轮廓转成层叠彩纸，导出 3:4 全出血 PNG。

## 直接运行

双击 `index.html` 即可离线使用。所有 CSS、脚本和示例照片均内嵌；不需要安装依赖，不需要 API Key，不会上传照片。

GitHub Pages 发布设置：选择 `Deploy from a branch` → `main` → `/(root)`。网页不要求登录 GitHub 或 ChatGPT。

## 功能

- 等比例 3:4 裁切：横向、纵向取景与放大，不拉伸图片。
- 4–10 层剪纸；可调形状概括、厚度、纤维与窄纸条节奏。
- 4 组配色与独立纸色编辑，随机配色。
- 可选飞鸟或纸舟尺度参照；原图对比、恢复默认。
- 1200×1600、1800×2400、2400×3200 PNG。导出重新绘制轮廓，不放大预览截图。导出没有文字，不包含作者署名或界面内容。

## 实现与边界

Canvas 2D + 本地 Blob Web Worker。低分辨率分析照片亮度，平滑分层，提取轮廓并简化为曲线路径；预览及导出以目标尺寸重新绘制路径。纹理使用固定种子的本地噪声与纤维线条。

它是基于照片的风格化滤镜，保留照片大致地貌，不具备 AI 场景理解或重新设计地形的能力。复杂照片细节可能简化成色块。

## 验证

Microsoft Edge / Playwright：检查各参数造成实际像素变化；JPG 和 PNG 上传；3:4 等比例裁切；1800×2400 PNG 实际下载；手机 390px 无横向溢出；file:// 离线运行；无第三方请求、无脚本错误。

WebMCP 按 `document.modelContext` 特性检测，提供 `adjust_paper_poster` 批量参数工具，严格校验后更新与界面共用状态。当前 Edge 无原生 WebMCP 支持；通过测试 shim 验证注册、有效调用和无效参数拒绝，未声称原生浏览器兼容性已验证。

## 示例照片

Tom Allport / Unsplash，1600×1067。

来源：https://unsplash.com/photos/a-river-surrounded-by-trees-and-mountains-Yh8_B8NlcFU

许可：https://unsplash.com/license

作者：德里克文
