# 人生K线 | Life Destiny K-Line

**将您的一生运势绘制成K线图，洞悉命运起伏，预见人生轨迹。**

> Visualize your life's fortune as a candlestick (K-Line) chart — combining traditional Chinese BaZi astrology with modern financial visualization.

Twitter/X: [@0xsakura666](https://twitter.com/0xsakura666)

---

## ✨ 功能特性 | Features

- 📊 **人生K线图** — 将 1–100 岁的运势数据渲染为类股票K线图（每根K线代表一个流年）
- 🔮 **八字命理分析** — 事业、财富、婚姻、健康、六亲五大维度评分与详批
- 🤖 **AI 驱动** — 接入任意兼容 OpenAI Chat Completions API 的大模型（支持 OpenRouter、本地模型等）
- 🎯 **大运排盘** — 支持顺行 / 逆行，精准推导十步大运序列
- 📱 **响应式设计** — 适配桌面端和移动端
- 🔑 **自带密钥** — 用户自行填写 API Key，数据不经过任何中间服务器

---

## 🚀 快速开始 | Quick Start

### 在线体验 | Live Demo

访问 GitHub Pages 部署版本：**https://huihuilili.github.io/lifekline/**

### 本地运行 | Local Development

**前置要求：** Node.js 18+，npm 或 pnpm

```bash
# 1. 克隆项目
git clone https://github.com/huihuilili/lifekline.git
cd lifekline

# 2. 安装依赖
npm install

# 3. 启动开发服务器
npm run dev
```

访问 `http://localhost:5173` 即可使用。

### 构建生产版本 | Build for Production

```bash
npm run build
# 产物在 dist/ 目录
npm run preview  # 本地预览构建产物
```

---

## 📖 使用说明 | How to Use

### 第一步：获取 API Key

本项目需要一个兼容 **OpenAI Chat Completions API** 的密钥。推荐以下渠道：

| 服务 | 地址 | 说明 |
|------|------|------|
| **OpenRouter** | https://openrouter.ai | 聚合多家模型，支持 Gemini、Claude、GPT 等 |
| **硅基流动** | https://siliconflow.cn | 国内可访问，提供 Qwen、DeepSeek 等 |
| **任意 OpenAI 兼容中转** | 自行填写 | 只要支持 `/chat/completions` 端点即可 |

> ⚠️ **注意**：API Key 仅在您的浏览器中本地使用，不会上传至任何服务器。

### 第二步：排四柱八字

为确保准确性，建议使用专业软件排盘，而非依赖 AI：

1. 访问 **[在线排盘工具](https://pcbz.iwzwh.com/#/paipan/index)**，输入出生信息
2. 记录**年柱、月柱、日柱、时柱**（各两个汉字，如：甲子、丙寅）
3. 记录**起运年龄**（虚岁）和**第一步大运**干支

### 第三步：填写表单并生成

在页面表单中依次填入：
- **基本信息**：姓名（可选）、性别
- **出生年份**：公历年份（如 1990）
- **四柱干支**：年柱 / 月柱 / 日柱 / 时柱
- **大运信息**：起运年龄、第一步大运
- **模型接口设置**：模型名、API Base URL、API Key

点击"**生成人生K线**"，等待 3–5 分钟即可获得分析结果。

---

## ⚙️ 模型接口配置 | API Configuration

| 字段 | 默认值 | 说明 |
|------|--------|------|
| **使用模型** | `google/gemini-3-pro-preview` | OpenRouter 模型名，或其他服务支持的模型 ID |
| **API Base URL** | `https://openrouter.ai/api/v1` | 兼容 OpenAI 的 API 根地址（勿带末尾斜杠） |
| **API Key** | *(留空)* | 对应服务的密钥，格式通常为 `sk-...` |

**推荐模型（效果好）：**
- `google/gemini-2.5-pro-preview` — Gemini 最强版（推荐，效果最佳）
- `google/gemini-2.0-flash` — 速度快，成本低
- `anthropic/claude-sonnet-4-5` — Claude 系列，中文理解好
- `deepseek/deepseek-chat` — 国产模型，中文表现优秀

---

## 🏗️ 技术架构 | Tech Stack

| 技术 | 版本 | 用途 |
|------|------|------|
| React | 19 | UI 框架 |
| TypeScript | 5 | 类型安全 |
| Vite | 5 | 构建工具 |
| Tailwind CSS | 3 | 样式 |
| Recharts | 2 | K线图表渲染 |
| Lucide React | 0.5+ | 图标库 |

**核心文件说明：**

```
├── App.tsx                    # 根组件，管理全局状态与流程
├── types.ts                   # TypeScript 类型定义
├── constants.ts               # 系统提示词与配置常量
├── components/
│   ├── BaziForm.tsx           # 输入表单（四柱 + 大运 + API 配置）
│   ├── LifeKLineChart.tsx     # K线图渲染组件
│   └── AnalysisResult.tsx     # 命理分析报告展示
└── services/
    └── geminiService.ts       # API 调用与响应解析
```

---

## 📊 K线图说明 | Chart Legend

| 颜色 | 含义 | 条件 |
|------|------|------|
| 🔴 **红色 K线** | 吉运（上涨）| `close > open` |
| 🟢 **绿色 K线** | 凶运（下跌）| `close < open` |

> 遵循中国股市配色惯例（红涨绿跌）。点击任意 K 线可查看该流年的详细批断。

---

## ⚠️ 免责声明 | Disclaimer

本项目仅供**娱乐与文化研究**，请勿迷信。命理学是古代哲学工具，不能替代专业建议。

> 一命二运三风水，四积阴德五读书，六名七相八敬神，九遇贵人十养生。

---

## 🤝 贡献 | Contributing

欢迎提交 Issue 和 Pull Request！

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/your-feature`)
3. 提交更改 (`git commit -m 'feat: add your feature'`)
4. 推送分支 (`git push origin feature/your-feature`)
5. 开启 Pull Request

---

## 📄 License

MIT License © 2024 [@0xsakura666](https://github.com/0xsakura666)
