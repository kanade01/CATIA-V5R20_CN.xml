# GB 工程图标准（CATIA V5）安装与使用说明

本目录中的 **GB.xml** 是由 CATIA V5 R20 自带的国际标准 `ISO.xml` 转换而来的**国标（GB）工程图样式标准**文件。
CATIA 以**文件名**作为标准名称，因此装入后标准列表中会直接出现 **GB**。

本包内容：

| 文件 | 说明 |
| --- | --- |
| `GB.xml` | 国标工程图标准（可直接安装使用） |
| `ISO_orig.xml` | 原始 ISO 标准备份（生成 GB.xml 的基准） |
| `build.js` | 生成脚本：`node build.js ISO_orig.xml GB.xml`，可自行改规则后重新生成 |
| `verify.js` | 校验脚本：逐叶子节点对比新旧文件 `node verify.js ISO_orig.xml GB.xml` |
| `CHANGES.md` | 变更清单（GB 条款 ↔ 参数 ↔ 新旧值） |

---

## 一、安装（3 步）

1. **备份**现有标准目录（只需做一次）：

   ```
   D:\CATIA V5 R20\Dassault Systemes\B20\intel_a\resources\standard\drafting\
   ```

   把整个 `drafting` 文件夹复制一份，例如复制为 `drafting_backup`。

2. **复制** `GB.xml` 到该目录，与 `ISO.xml`、`ANSI.xml`、`JIS.xml` 等并列：

   ```
   D:\CATIA V5 R20\Dassault Systemes\B20\intel_a\resources\standard\drafting\GB.xml
   ```

3. **重启 CATIA**，然后任选一种方式选用 GB：

   - 新图纸：`文件 > 新建 > Drawing` 时在“绘图标准”下拉框中选择 **GB**；
   - 已有图纸：`文件 > 页面设置`（Page Setup）→ “标准”下拉框改为 **GB**；
   - 设为默认：`工具 > 选项 > 机械设计 > 工程制图 > 标准`，把“标准”改为 **GB**。

> 若下拉框中没有出现 GB：确认文件名确为 `GB.xml`（区分大小写不敏感但扩展名必须是 .xml）、路径正确、且已完全退出并重启 CATIA。

## 二、这个标准做了什么

依据 GB/T 14689（图纸幅面）、GB/T 14691（字体）、GB/T 4457.4（图线）、
GB/T 4458.4（尺寸注法）、GB/T 131（表面结构）等，主要修改：

- **线宽**：粗实线 = 0.70 mm（`LineThickness` 索引 3），细线 = 0.35 mm（索引 2），即 GB 的 **d : d/2 = 2 : 1**；
- **尺寸终端**：由 ISO 的开口箭头（`SimpleArrow`）改为 GB 的**实心箭头**（`FilledArrow`），箭头长 4d = 2.8 mm、顶角约 14°；
- **中心线/轴线/螺纹线**：超出轮廓固定 3 mm（GB 规定 2~5 mm）；
- **尺寸线间距**：7 mm（GB 不小于 5~7 mm）；
- **字体**：全部文字样式默认 **仿宋**（GB 长仿宋体系），字高系列加入 GB 的 **1.8 mm**（1.8/2.5/3.5/5/7/10/14/20）；
- **A4 默认竖装**（A0~A3 仍为横装）；
- **剖面线**：细实线 0.35 mm，默认剖面线图样改为 `STD 3`（间距 3 mm）；
- **粗糙度**符号按细实线绘制；投影方向已为 GB 的**第一角投影**（ISO.xml 原本就是 First angle，无需改动）。

详细逐条对照见 [CHANGES.md](CHANGES.md)。

## 三、注意事项与未包含内容

1. **幅面名称保持 "A0 ISO" ~ "C5 ISO" 未改**。
   CATIA 的图框、标题栏资源按这个名称与 `SheetFormat/Formats` 条目绑定，若改成 "A0 GB"，
   一方面 CATIA 找不到对应图框而报错，另一方面会导致图纸无边框。标准名由**文件名 GB.xml** 体现，不影响使用。
2. **字体 `FangSong`**：需要系统安装“仿宋”（中文 Windows 自带）。若单位要求“长仿宋体”，
   安装该字体后把 `GB.xml` 中所有 `FangSong` 替换为字体实际名称即可（共 17 处）。
3. **本文件不含 GB 图框与标题栏**。CATIA 的图框/标题栏是独立资源（`resources\standard\...` 下的图框与 Title Block），
   ISO.xml 里没有定义，因此本包只覆盖**样式参数**。要 GB 风格的图框/标题栏，需另做 CATDrawing 图框模板或用 CATIA 的框架编辑器制作。
4. **B4/B5/C5 幅面保留**（ISO.xml 原有），GB 未规定这两种，可忽略或删除。
5. **加长幅面**（A3×3、A4×4 等）未加入，需要在 CATIA 中按需自定义图纸尺寸。
6. **字体大小系列被重排**：新增 1.8 后，原有槽位整体后移一位，这属于预期行为（可用 `verify.js` 看到 8 处变化）。
7. 标准中的 `ParentStandard` 保持 `ISO`（改成 `GB` 会让 CATIA 去找名为 GB 的父标准而报错）。

## 四、自定义

```bash
node build.js ISO_orig.xml GB.xml     # 重新生成
node verify.js ISO_orig.xml GB.xml    # 查看逐项差异（输出 diff.json）
```

修改 `build.js` 中的规则即可（例如把汉字字体改为 `SimSun`、线宽改为 1.0/0.5、
箭头长度改为其他值），生成后可先在临时目录试用，确认无误再覆盖正式标准目录。
