这个项目本质上是一个基于 Web 的 ECharts 实时开发与预览环境。它的核心目标是提供一个类似于 ECharts 官方示例（Gallery）的本地化工作台，方便开发者在本地快速编写、调试和导出图表。

<img width="1912" height="946" alt="image" src="https://github.com/user-attachments/assets/03473719-d136-4730-bf07-ac420cdd8161" />


以下是该项目的四大核心模块介绍：

1. 实时编辑与代码执行 (Editor)
项目集成了 Monaco Editor（VS Code 的核心编辑器），支持 JavaScript 和 TypeScript 语法。

代码注入机制：利用 new Function 技术，将用户编写的代码动态注入到预设的环境中。

环境预设：自动为代码环境注入了 echarts 实例、myChart 对象、jQuery 以及 ROOT_PATH。这意味着你可以直接粘贴官方示例代码而无需任何修改。

2. 动态渲染容器 (Preview)
右侧预览区负责承载图表的生命周期管理。

智能重绘：每次点击“运行”时，系统会先执行 myChart.dispose() 销毁旧实例，再初始化新实例，防止内存泄漏和配置项污染。

深色模式一键切换：支持在渲染时动态更改主题。

3. 灵活的布局管理 (Layout)
采用了经典的三栏式布局，并实现了原生的拖拽缩放逻辑：

左侧示例库：分类展示常用的 ECharts 模板。

中间编辑器：代码编写区域。

右侧预览区：结果展示。

双向调节：用户可以通过拖拽分割线（Resizer）实时调整各区域的比例，编辑器和图表会自动触发 resize() 以适应新尺寸。

4. 增强的兼容性修复
针对你之前遇到的“加载中”和“不出东西”的问题，该项目特别优化了：

异步支持：即使代码中包含 setTimeout 或异步获取 JSON 数据，环境也能通过 showLoading 状态正确处理。

本地服务器友好：针对跨域问题做了变量适配，建议配合 Python 或 Node.js 本地服务器使用。
