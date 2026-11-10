# 黄硕 · 在线简历

一份数据驱动的单页简历：网页可直接查看，浏览器打印即可导出 PDF。

线上地址：**https://shuo-huge.github.io/resume/**

## 文件结构

| 文件 | 作用 |
|---|---|
| `resume.json` | **唯一内容源**。所有文字、经历、链接都在这里改 |
| `index.html` | 页面模板、样式与渲染逻辑（一般不用动） |
| `.nojekyll` | 告诉 GitHub Pages 不要走 Jekyll 处理 |

## 修改内容

直接编辑 `resume.json`，保存后刷新页面即可。常用字段：

- `basics`：姓名、职位、地点、邮箱、LinkedIn、GitHub、个人简介
- `skills`：技能分组
- `experience`：工作经历（公司、职位、时间、地点、要点列表）
- `opensource`：开源项目
- `education`：教育背景
- `notes`：待补事项（不会显示在页面上，给 AI / 自己看的备忘）

### 当前待补字段（见 `notes`）

1. FEEL2NICE 的起始年份（`experience[0].period`）
2. 比亚迪的任职年份（`experience[1].period`）
3. 陕西师范大学的专业、学位与毕业年份
4. 联系邮箱 / 电话（`basics.email`，留空则页面自动隐藏）

> 时间字段当前写着 `TODO：…`，会直接显示在页面上；补齐后记得删掉 TODO 标记。

## 本地预览

`index.html` 通过 `fetch` 读取 `resume.json`，直接双击打开会被浏览器拦截。请在目录里起一个静态服务器：

```bash
cd resume
python -m http.server 8080
# 打开 http://localhost:8080
```

## 导出 PDF

1. 打开线上页面（或本地预览）
2. 点右上角 **导出 PDF**
3. 在打印对话框里选择「另存为 PDF」、纸张 A4、边距默认
4. 关闭「页眉和页脚」效果更好

页面已写好 `@page` 与打印样式，自动隐藏按钮、去掉阴影，并按 A4 排版。

## 让 AI 完善

把这个目录交给任意 AI（或直接在本项目里提问），提示词可以这样说：

> 这是 `resume.json`，请根据我的补充信息完善它。保持现有字段结构不变；时间统一写成 `2021 — 至今` 这种格式；每条工作要点用动词开头、尽量带量化结果；不要编造不存在的数据，缺失信息放进 `notes`。

改完 JSON 后：

```bash
git add resume.json
git commit -m "update resume"
git push
```

GitHub Pages 通常 1 分钟内自动更新（首次部署可能需要几分钟）。

## 部署

仓库已开启 GitHub Pages（分支 `main`，根目录）。如果换了仓库或分支，去 **Settings → Pages** 重新选择即可。

## 隐私说明

仓库是公开的：姓名、所在城市、公司名、GitHub/LinkedIn 都会公开可见。不要往 `resume.json` 里放手机号、住址等敏感信息，除非你确认要公开。
