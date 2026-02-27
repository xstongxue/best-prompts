# 公众号封面 Draw.io 生成

为公众号、技术博客等自媒体内容生成 Draw.io (.drawio) 格式的封面布局，支持多种常用尺寸比例，可直接保存为 `.drawio` 文件在 Draw.io 中打开、编辑并导出为 PNG/JPG。

## 适用场景

- 公众号文章封面图、结尾总结图
- 技术博客配图、B 站封面、小红书图文
- 需要指定比例、可编辑的封面布局
- **串联使用**：配合 [公众号文章写作](wechat-article-writer-prompt.md)，其「排版建议」中的【封面图】【结尾图】需求可直接作为本 Prompt 的输入；正文插图（步骤图/演示图）请用 [公众号文章插图 Draw.io 生成](wechat-article-illustration-prompt.md)

## 支持尺寸比例


| 比例         | 用途             | 画布尺寸（Draw.io） |
| ---------- | -------------- | ------------- |
| **1:1**    | 正方形，头像、图标、卡片   | 900×900       |
| **16:9**   | 横版封面、B 站封面、PPT | 1920×1080     |
| **9:16**   | 竖版封面、小红书、短视频   | 1080×1920     |
| **4:3**    | 传统横版、文章插图      | 1200×900      |
| **3:4**    | 竖版插图、卡片        | 900×1200      |
| **2.35:1** | 电影宽银幕、氛围感横图    | 1920×817      |


## Prompt

```
# Role
你是一位精通 Draw.io（diagrams.net）XML 格式的封面设计专家。你能够为公众号、技术博客等自媒体生成**标准的 .drawio 封面文件**（mxGraph XML 格式），确保 XML 格式严格正确、无标签错误，可直接在 Draw.io 中打开、编辑并导出为 PNG/JPG 用作配图。

# Task
根据我提供的【配图需求】，生成符合 Draw.io 语法的 .drawio 文件内容，包含背景、文字占位区、装饰元素等封面布局。

# 适用场景（供参考）
公众号文章封面/结尾图、技术博客配图、B 站封面、小红书图文、PPT 配图等，需指定比例且可编辑的封面布局。

# Constraints

## 1. XML 格式严格性
- 所有标签必须正确闭合：`<mxCell>` 对应 `</mxCell>`，绝不能写成 `</mCell>`
- 使用 `vertex="1"` 标记图形节点
- 每个元素必须有唯一 `id`，从 0 开始递增
- 特殊字符必须转义：`&` → `&`，`<` → `<`，`>` → `>`

## 2. 标准文件结构
xml
<mxfile host="app.diagrams.net">
  <diagram name="封面名称" id="封面id">
    <mxGraphModel dx="1200" dy="800" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="宽度" pageHeight="高度" background="#ffffff">
      <root>
        <mxCell id="0"/>
        <mxCell id="1" parent="0"/>
        <!-- 所有图形元素从 id="2" 开始：背景、文字区、装饰等 -->
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>


## 3. 封面布局元素
- **背景**：全画布矩形，填充主题色或渐变（Draw.io 支持 `fillColor`、`gradientColor`）
- **标题区**：文本框占位，预留主标题/副标题区域。**重点文字必须足够大**：主标题 56–80pt，副标题 28–40pt，确保公众号小图预览时仍可清晰辨识
- **装饰**：简洁几何形状（圆角矩形、线条、色块）增强层次感
- **留白**：确保重要区域不被遮挡，适合公众号小图预览

## 4. 配色方案（必须参考）
根据用户指定的【配色偏好】或从主题推断，**必须**从下表选择并应用对应色值到 `fillColor`、`fontColor`、`gradientColor` 等 style 属性：

- **科技/编程类**：深色背景 #1a1a2e、科技蓝 #4A90D9、青色点缀 #00D9FF、紫色 #9B59B6
- **教程/干货类**：浅色背景 #F8F9FA、主色 #2C3E50、辅助色 #3498DB、强调色 #E74C3C
- **暖色/生活类**：背景 #FFF8F0、主色 #E67E22、辅助色 #F39C12、点缀 #D35400
- **商务/金融类**：深蓝 #1E3A5F、金色 #D4AF37、灰 #5D6D7E、浅底 #ECF0F1
- **清新/文艺类**：薄荷绿 #A8E6CF、浅蓝 #89CFF0、米白 #FAF3E0、珊瑚 #FF6B6B
- **极简/黑白**：黑 #2C2C2C、白 #FFFFFF、灰阶 #7F8C8D、#BDC3C7
- **活力/年轻**：亮橙 #FF6B35、粉 #FF9FF3、紫 #9B59B6、青 #48C9B0
- **品牌色参考**：微信绿 #07C160、知乎蓝 #0084FF、B 站粉 #FB7299、GitHub 紫 #6E5494

## 5. 尺寸比例（必选其一）
用户未指定时默认 **16:9**。pageWidth 与 pageHeight 需严格符合下表，并按用途调整布局（如 9:16 竖版需纵向排版）：

| 比例 | pageWidth | pageHeight | 典型用途 |
|------|-----------|------------|----------|
| 1:1 | 900 | 900 | 头像、图标、卡片 |
| 16:9 | 1920 | 1080 | 横版封面、B 站、PPT |
| 9:16 | 1080 | 1920 | 竖版封面、小红书、短视频 |
| 4:3 | 1200 | 900 | 传统横版、文章插图 |
| 3:4 | 900 | 1200 | 竖版插图、卡片 |
| 2.35:1 | 1920 | 817 | 电影宽银幕、氛围横图 |

# Output Format

1. **Draw.io 文件内容**：完整 mxGraph XML，可保存为 `.drawio` 文件
2. **封面说明**：1–2 句中文，说明布局用途与风格
3. **使用说明**：保存为 `.drawio` → 在 Draw.io 中打开 → 编辑文字/颜色 → 导出 PNG/JPG

# Input
【配图需求】：
- 用途：[封面图 / 结尾图 / 其他]
- 比例：[1:1 / 16:9 / 9:16 / 4:3 / 3:4 / 2.35:1]
- 主题/内容：[在此处描述封面要表达的内容、关键词、风格偏好]
- 配色偏好：[科技/编程类 / 教程/干货类 / 暖色/生活类 / 商务/金融类 / 清新/文艺类 / 极简/黑白 / 活力/年轻 / 品牌色+名称]；未指定则根据主题推断
- 参考元素（可选）：[如：代码、AI、某品牌色等]
```

---

## 使用示例

**输入：**

```
用途：封面图
比例：16:9
主题/内容：Python 入门教程，简洁技术风，关键词"代码""学习""实战"
配色偏好：教程/干货类
参考元素：Python logo、代码括号装饰
```

**输出示例（Gemini）：**

这里为您生成的 Draw.io XML 封面文件。此设计采用了**“左文右图”的经典技术教程布局**，配色严格遵循【教程/干货类】方案（浅底深字，蓝红点缀），并结合了 Python 代码元素。

### 1. 封面说明

- **布局风格**：简洁技术风。左侧为大号标题区，右侧为模拟的代码终端窗口，背景辅以淡色代码水印。
- **配色方案**：背景 `#F8F9FA`（护眼浅灰），主文字 `#2C3E50`（深蓝灰），强调色 `#3498DB`（科技蓝）与 `#E74C3C`（警示红/强调）。
- **适用场景**：公众号首图、B站视频封面、技术博客头图。

### 2. Draw.io 文件内容 (XML)

请复制以下代码块中的全部内容：

```xml
<mxfile host="app.diagrams.net">
  <diagram name="Python教程封面" id="PythonCover01">
    <mxGraphModel dx="1920" dy="1080" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="1920" pageHeight="1080" background="#F8F9FA">
      <root>
        <mxCell id="0"/>
        <mxCell id="1" parent="0"/>
        
        <!-- ================= 背景层 ================= -->
        <!-- 1. 全局背景 -->
        <mxCell id="2" value="" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#F8F9FA;strokeColor=none;" vertex="1" parent="1">
          <mxGeometry x="0" y="0" width="1920" height="1080" as="geometry"/>
        </mxCell>
        
        <!-- 2. 背景装饰：巨大的括号水印 (左侧) -->
        <mxCell id="3" value="{" style="text;html=1;align=center;verticalAlign=middle;resizable=0;points=[];autosize=1;strokeColor=none;fillColor=none;fontSize=800;fontColor=#EAECEE;fontFamily=Consolas;" vertex="1" parent="1">
          <mxGeometry x="-100" y="80" width="400" height="1000" as="geometry"/>
        </mxCell>
        
         <!-- 3. 背景装饰：巨大的括号水印 (右侧) -->
        <mxCell id="4" value="}" style="text;html=1;align=center;verticalAlign=middle;resizable=0;points=[];autosize=1;strokeColor=none;fillColor=none;fontSize=800;fontColor=#EAECEE;fontFamily=Consolas;" vertex="1" parent="1">
          <mxGeometry x="1600" y="80" width="400" height="1000" as="geometry"/>
        </mxCell>

        <!-- ================= 主要图形层 (右侧代码窗口) ================= -->
        <!-- 4. 终端窗口阴影 -->
        <mxCell id="5" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#BDC3C7;strokeColor=none;arcSize=5;opacity=50;" vertex="1" parent="1">
          <mxGeometry x="960" y="240" width="820" height="620" as="geometry"/>
        </mxCell>

        <!-- 5. 终端窗口主体 -->
        <mxCell id="6" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#2C3E50;strokeColor=none;arcSize=4;" vertex="1" parent="1">
          <mxGeometry x="940" y="220" width="820" height="600" as="geometry"/>
        </mxCell>

        <!-- 6. 终端顶部栏 -->
        <mxCell id="7" value="" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#34495E;strokeColor=none;arcSize=4;" vertex="1" parent="1">
          <mxGeometry x="940" y="220" width="820" height="60" as="geometry"/>
        </mxCell>
        <!-- 遮挡顶部栏下半部分的圆角，使其变直角 -->
        <mxCell id="8" value="" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#34495E;strokeColor=none;" vertex="1" parent="1">
          <mxGeometry x="940" y="250" width="820" height="30" as="geometry"/>
        </mxCell>

        <!-- 7. 窗口控制按钮 (红黄绿) -->
        <mxCell id="9" value="" style="ellipse;whiteSpace=wrap;html=1;aspect=fixed;fillColor=#E74C3C;strokeColor=none;" vertex="1" parent="1">
          <mxGeometry x="970" y="235" width="30" height="30" as="geometry"/>
        </mxCell>
        <mxCell id="10" value="" style="ellipse;whiteSpace=wrap;html=1;aspect=fixed;fillColor=#F1C40F;strokeColor=none;" vertex="1" parent="1">
          <mxGeometry x="1020" y="235" width="30" height="30" as="geometry"/>
        </mxCell>
        <mxCell id="11" value="" style="ellipse;whiteSpace=wrap;html=1;aspect=fixed;fillColor=#2ECC71;strokeColor=none;" vertex="1" parent="1">
          <mxGeometry x="1070" y="235" width="30" height="30" as="geometry"/>
        </mxCell>

        <!-- 8. 代码内容 (模拟Python代码) -->
        <mxCell id="12" value="<font style="font-size: 40px" face="Courier New"><font color="#e74c3c">def</font> <font color="#3498db">start_learning</font>():<br>&nbsp; &nbsp; topic = <font color="#2ecc71">"Python Tutorial"</font><br>&nbsp; &nbsp; level = <font color="#f1c40f">0</font><br>&nbsp; &nbsp; <font color="#e74c3c">print</font>(<font color="#2ecc71">"Hello World!"</font>)<br><br><font color="#bdc3c7"># 开始你的编程之旅<br># 实战案例解析<br>&gt;&nbsp;</font><font color="#e74c3c">_</font></font>" style="text;html=1;align=left;verticalAlign=top;resizable=0;points=[];autosize=1;strokeColor=none;fillColor=none;" vertex="1" parent="1">
          <mxGeometry x="980" y="320" width="700" height="400" as="geometry"/>
        </mxCell>

        <!-- ================= 文字标题层 (左侧) ================= -->
        
        <!-- 9. 顶部小标签 -->
        <mxCell id="13" value="PROGRAMMING" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#E74C3C;strokeColor=none;fontColor=#FFFFFF;fontStyle=1;fontSize=24;spacingLeft=10;spacingRight=10;" vertex="1" parent="1">
          <mxGeometry x="140" y="300" width="220" height="50" as="geometry"/>
        </mxCell>

        <!-- 10. 主标题 - 第一行 -->
        <mxCell id="14" value="Python" style="text;html=1;align=left;verticalAlign=middle;resizable=0;points=[];autosize=1;strokeColor=none;fillColor=none;fontSize=180;fontStyle=1;fontColor=#2C3E50;" vertex="1" parent="1">
          <mxGeometry x="130" y="360" width="600" height="200" as="geometry"/>
        </mxCell>

        <!-- 11. 主标题 - 第二行 -->
        <mxCell id="15" value="入门教程" style="text;html=1;align=left;verticalAlign=middle;resizable=0;points=[];autosize=1;strokeColor=none;fillColor=none;fontSize=160;fontStyle=1;fontColor=#2C3E50;" vertex="1" parent="1">
          <mxGeometry x="130" y="540" width="700" height="180" as="geometry"/>
        </mxCell>

        <!-- 12. 装饰线条 -->
        <mxCell id="16" value="" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#3498DB;strokeColor=none;" vertex="1" parent="1">
          <mxGeometry x="140" y="740" width="120" height="10" as="geometry"/>
        </mxCell>

        <!-- 13. 副标题/卖点 -->
        <mxCell id="17" value="零基础 · 实战演练 · 源码解析" style="text;html=1;align=left;verticalAlign=middle;resizable=0;points=[];autosize=1;strokeColor=none;fillColor=none;fontSize=45;fontColor=#7F8C8D;fontStyle=0;" vertex="1" parent="1">
          <mxGeometry x="140" y="770" width="700" height="60" as="geometry"/>
        </mxCell>

      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
```

预览图：
![](https://pic1.imgdb.cn/item/69a14041ec0a30908d678c73.png)


### 3. 使用说明

1. **保存**：将上面的 XML 代码复制并保存为 `python_cover.drawio`（或者 `.xml`）文件。
2. **打开**：访问 [draw.io (diagrams.net)](https://app.diagrams.net/)，选择“打开现有图表”并加载该文件。
3. **编辑**：
  - 双击左侧文字可修改标题内容。
  - 双击右侧黑色区域的文字，可以编辑“代码内容”。
4. **导出**：
  - 点击菜单栏 `File` -> `Export as` -> `PNG` (或 `JPEG`)。
  - **重要**：导出时确保 `Zoom` 至少为 `100%`，建议勾选 `Include a copy of my diagram` 以便后续再次编辑。

