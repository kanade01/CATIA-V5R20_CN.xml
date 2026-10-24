# ISO.xml → GB.xml 变更清单

生成方式：`node build.js ISO_orig.xml GB.xml`；校验：`node verify.js ISO_orig.xml GB.xml`
共 **101** 处叶子节点取值变化，节点结构与节点数完全不变（解析器校验通过）。
基准：CATIA V5 R20 自带 `D:\CATIA V5 R20\Dassault Systemes\B20\intel_a\resources\standard\drafting\ISO.xml`

> 说明：CATIA 的线宽、字体等以“索引/名称”引用，表中括号内为换算后实际效果。
> 数值依据 GB/T 14689（幅面）、GB/T 14691（字体）、GB/T 4457.4（图线）、GB/T 4458.4（尺寸注法）、GB/T 131（表面结构）。

## 剖面线：细实线 + 间距 3 mm

依据：**GB/T 4457.4 / GB/T 17453**。hatchings 的 thickness1 1 → 2（细实线 0.35mm）；默认剖面图样 "STD 5"(5mm 间距) → "STD 3"(3mm 间距)。

| 参数路径 | 旧值 | 新值 |
| --- | --- | --- |
| `drafting/Styles/AreaFill/Default/Pattern/std:strval` | STD 5 | STD 3 |
| `drafting/Patterns/hatching/hatchings` | STD 5: thickness1 1 | STD 5: thickness1 2 |
| `drafting/Patterns/hatching/hatchings` | STD 10: thickness1 1 | STD 10: thickness1 2 |
| `drafting/Patterns/hatching/hatchings` | STD 20: thickness1 1 | STD 20: thickness1 2 |
| `drafting/Patterns/hatching/hatchings` | STD 1: thickness1 1 | STD 1: thickness1 2 |
| `drafting/Patterns/hatching/hatchings` | STD 2: thickness1 1 | STD 2: thickness1 2 |
| `drafting/Patterns/hatching/hatchings` | STD 3: thickness1 1 | STD 3: thickness1 2 |
| `drafting/Patterns/hatching/hatchings` | STD 4: thickness1 1 | STD 4: thickness1 2 |
| `drafting/Patterns/hatching/hatchings` | STD 6: thickness1 1 | STD 6: thickness1 2 |
| `drafting/Patterns/hatching/hatchings` | STD 8: thickness1 1 | STD 8: thickness1 2 |

## 粗糙度符号用细实线

依据：**GB/T 131**。LineThickness 1 → 2，符号线宽与字高协调（细实线）。

| 参数路径 | 旧值 | 新值 |
| --- | --- | --- |
| `drafting/Annotation/Roughness/ExtensionLine/Thickness/LineThickness/std:intval` | 1 | 2 |

## 线宽（GB/T 4457.4：d : d/2 = 2 : 1，d = 0.7 mm）

依据：**GB/T 4457.4**。细线 1(0.13mm) → 2(0.35mm)，粗线 2(0.35mm) → 3(0.70mm)。CATIA 线宽是“索引”，实际值见 LineThickness 表；本表 2=0.35、3=0.70，恰为 GB 的 d/2 与 d。

| 参数路径 | 旧值 | 新值 |
| --- | --- | --- |
| `drafting/Styles/ConstructionCurve/Default/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/Curve/Default/Thickness/std:intval` | 2 | 3 |
| `drafting/Styles/DistanceLengthDimension/Default/DimensionLine/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/DistanceLengthDimension/Default/Symbols/Symbol1/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/DistanceLengthDimension/Default/Symbols/Symbol2/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/DistanceLengthDimension/Default/ExtensionLine/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/AngleDimension/Default/DimensionLine/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/AngleDimension/Default/Symbols/Symbol1/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/AngleDimension/Default/Symbols/Symbol2/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/AngleDimension/Default/ExtensionLine/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/RadiusDimension/Default/DimensionLine/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/RadiusDimension/Default/Symbols/Symbol1/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/RadiusDimension/Default/Symbols/Symbol2/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/RadiusDimension/Default/ExtensionLine/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/DiameterDimension/Default/DimensionLine/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/DiameterDimension/Default/Symbols/Symbol1/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/DiameterDimension/Default/Symbols/Symbol2/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/DiameterDimension/Default/ExtensionLine/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/ChamferDimension/Default/DimensionLine/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/ChamferDimension/Default/Symbols/Symbol1/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/ChamferDimension/Default/Symbols/Symbol2/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/ChamferDimension/Default/ExtensionLine/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/Text/Default/Graphic/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/Table/Default/Graphic/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/DatumFeature/Default/Graphic/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/DatumTarget/Default/Graphic/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/Tolerance/Default/Graphic/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/Balloon/Default/Graphic/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/RoughnessSymbol/Default/Graphic/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/WeldingSymbol/Default/Graphic/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/AxisLine/Default/Graphic/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/CenterLine/Default/Graphic/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/Thread/Default/Graphic/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/Arrow/Default/Graphic/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/ProjectionCallout/Default/Profile/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/ProjectionCallout/Default/Corners/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/ProjectionCallout/Default/Arrows/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/SectionCallout/Default/Profile/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/SectionCallout/Default/Corners/Thickness/std:intval` | 4 | 3 |
| `drafting/Styles/SectionCallout/Default/Arrows/Thickness/std:intval` | 1 | 2 |
| `drafting/Styles/DetailCallout/Default/Thickness/std:intval` | 1 | 2 |
| `drafting/View/Generation/ThicknessIndex/std:intval` | 2 | 3 |

## 尺寸终端：实心箭头（GB/T 4458.4）

依据：**GB/T 4458.4**。ISO 的开口箭头 SimpleArrow → GB 的实心箭头 FilledArrow（共 5 个尺寸样式 × 2 端）。

| 参数路径 | 旧值 | 新值 |
| --- | --- | --- |
| `drafting/Styles/DistanceLengthDimension/Default/Symbols/Symbol1/Type/ArrowEndType` | SimpleArrow | FilledArrow |
| `drafting/Styles/DistanceLengthDimension/Default/Symbols/Symbol2/Type/ArrowEndType` | SimpleArrow | FilledArrow |
| `drafting/Styles/AngleDimension/Default/Symbols/Symbol1/Type/ArrowEndType` | SimpleArrow | FilledArrow |
| `drafting/Styles/AngleDimension/Default/Symbols/Symbol2/Type/ArrowEndType` | SimpleArrow | FilledArrow |
| `drafting/Styles/RadiusDimension/Default/Symbols/Symbol1/Type/ArrowEndType` | SimpleArrow | FilledArrow |
| `drafting/Styles/RadiusDimension/Default/Symbols/Symbol2/Type/ArrowEndType` | SimpleArrow | FilledArrow |
| `drafting/Styles/DiameterDimension/Default/Symbols/Symbol1/Type/ArrowEndType` | SimpleArrow | FilledArrow |
| `drafting/Styles/DiameterDimension/Default/Symbols/Symbol2/Type/ArrowEndType` | SimpleArrow | FilledArrow |
| `drafting/Styles/ChamferDimension/Default/Symbols/Symbol1/Type/ArrowEndType` | SimpleArrow | FilledArrow |
| `drafting/Styles/ChamferDimension/Default/Symbols/Symbol2/Type/ArrowEndType` | SimpleArrow | FilledArrow |

## 箭头尺寸（长 4d = 2.8 mm，宽 = d = 0.7 mm，顶角≈14°）

依据：**GB/T 4458.4**。Length 2 → 2.8；Angle 30° → 14°（宽长比 1:4，宽≈0.7 与粗实线同宽）；全局符号参数同步。

| 参数路径 | 旧值 | 新值 |
| --- | --- | --- |
| `drafting/DressUp/Symbols/FilledArrow/Length/std:floatval` | 2 | 2.8 |
| `drafting/DressUp/Symbols/FilledArrow/Angle/std:floatval` | 30 | 14 |
| `drafting/Dimension/SYMBFilledArrowSide/std:floatval` | 2 | 2.8 |
| `drafting/Dimension/SYMBFilledArrowAngle/std:floatval` | 30 | 14 |

## 中心线/轴线/螺纹线超出轮廓 3 mm（GB 规定 2~5 mm）

依据：**GB/T 4457.4**。改为固定超出长度 3.0 mm（原为自动 0.0），使中心线两端在轮廓外一致伸出。

| 参数路径 | 旧值 | 新值 |
| --- | --- | --- |
| `drafting/Styles/AxisLine/Default/OverRunAuto/YesNo` | Yes | No |
| `drafting/Styles/AxisLine/Default/OverRunLength/std:floatval` | 0.0 | 3.0 |
| `drafting/Styles/CenterLine/Default/OverRunAuto/YesNo` | Yes | No |
| `drafting/Styles/CenterLine/Default/OverRunLength/std:floatval` | 0.0 | 3.0 |
| `drafting/Styles/Thread/Default/OverRunAuto/YesNo` | Yes | No |
| `drafting/Styles/Thread/Default/OverRunLength/std:floatval` | 0.0 | 3.0 |

## 尺寸线间距 7 mm

依据：**GB/T 4458.4**。OffsetLinear 10.0 → 7.0（GB 要求尺寸线间距不小于 5~7 mm，取 7 便于排布）。

| 参数路径 | 旧值 | 新值 |
| --- | --- | --- |
| `drafting/Styles/DimensionsSystem/Default/OffsetLinear/std:floatval` | 10.0 | 7.0 |

## 字体：仿宋（GB/T 14691 长仿宋体系）

依据：**GB/T 14691**。原为空（跟随 CATIA 默认字体），统一设为 FangSong（仿宋）。如需长仿宋体请替换为对应字体名。

| 参数路径 | 旧值 | 新值 |
| --- | --- | --- |
| `drafting/Styles/DistanceLengthDimension/Default/Font/Name/std:strval` | (空) | FangSong |
| `drafting/Styles/AngleDimension/Default/Font/Name/std:strval` | (空) | FangSong |
| `drafting/Styles/RadiusDimension/Default/Font/Name/std:strval` | (空) | FangSong |
| `drafting/Styles/DiameterDimension/Default/Font/Name/std:strval` | (空) | FangSong |
| `drafting/Styles/ChamferDimension/Default/Font/Name/std:strval` | (空) | FangSong |
| `drafting/Styles/CoordinateDimension/Default/Font/Name/std:strval` | (空) | FangSong |
| `drafting/Styles/Text/Default/Font/Name/std:strval` | (空) | FangSong |
| `drafting/Styles/Table/Default/CellStyles/WholeTable/Font/Name/std:strval` | (空) | FangSong |
| `drafting/Styles/DatumFeature/Default/Font/Name/std:strval` | (空) | FangSong |
| `drafting/Styles/DatumTarget/Default/Font/Name/std:strval` | (空) | FangSong |
| `drafting/Styles/Tolerance/Default/Font/Name/std:strval` | (空) | FangSong |
| `drafting/Styles/Balloon/Default/Font/Name/std:strval` | (空) | FangSong |
| `drafting/Styles/RoughnessSymbol/Default/Font/Name/std:strval` | (空) | FangSong |
| `drafting/Styles/WeldingSymbol/Default/Font/Name/std:strval` | (空) | FangSong |
| `drafting/Styles/ProjectionCallout/Default/Text/Font/Name/std:strval` | (空) | FangSong |
| `drafting/Styles/SectionCallout/Default/Text/Font/Name/std:strval` | (空) | FangSong |
| `drafting/Styles/DetailCallout/Default/Text/Font/Name/std:strval` | (空) | FangSong |

## 字高系列加入 1.8 mm（GB/T 14691）

依据：**GB/T 14691**。GB 字高系列为 1.8/2.5/3.5/5/7/10/14/20，原 ISO 表缺 1.8；插入后原有槽位顺移一位。

| 参数路径 | 旧值 | 新值 |
| --- | --- | --- |
| `drafting/General/AllowedTextFontSizes/std:floatval` | 2.5 | 1.8 |
| `drafting/General/AllowedTextFontSizes/std:floatval` | 3.5 | 2.5 |
| `drafting/General/AllowedTextFontSizes/std:floatval` | 5.0 | 3.5 |
| `drafting/General/AllowedTextFontSizes/std:floatval` | 7.0 | 5.0 |
| `drafting/General/AllowedTextFontSizes/std:floatval` | 10.0 | 7.0 |
| `drafting/General/AllowedTextFontSizes/std:floatval` | 14.0 | 10.0 |
| `drafting/General/AllowedTextFontSizes/std:floatval` | 20.0 | 14.0 |
| `drafting/General/AllowedTextFontSizes/std:floatval` | 0.0 | 20.0 |

## A4 默认竖装（GB/T 14689）

依据：**GB/T 14689**。A4 图纸样式与幅面定义都改为竖装优先（PortraitByDefault）；A0~A3 保持横装。

| 参数路径 | 旧值 | 新值 |
| --- | --- | --- |
| `drafting/Styles/Sheet/A4 ISO/Orientation/SheetOrientation` | Landscape | Portrait |
| `drafting/SheetFormat/Formats` | A4 ISO: LandscapeByDefault | A4 ISO: PortraitByDefault |

## 保持不变（有意为之）

| 项目 | 现值 | 原因 |
| --- | --- | --- |
| ProjectionMethod | First angle | ISO.xml 原本就是第一角投影，已符合 GB |
| 幅面名称 | A0 ISO ~ C5 ISO | CATIA 图框/标题栏按此名称绑定，改名会找不到图框 |
| ParentStandard | ISO | 改为 GB 会使 CATIA 查找不存在的父标准 |
| ThreadRepresentation | Arc circle | 已是 GB 的 3/4 圆螺纹表示 |
| LineTypes (LT1~LT*) | 原样 | 线型定义已为 GB 常用形式（细实线/虚线/点画线/双点画线），未改 |
| B4/B5/C5 幅面 | 保留 | GB 未规定，保留不影响使用 |

## 已知未覆盖

- **图框与标题栏**：不在 ISO.xml 内（CATIA 独立图框资源），需另做模板；
- **加长幅面**（A3×3、A4×4…）：需在 CATIA 中自定义图纸尺寸；
- **BOM/明细栏**的 GB 版式：BomStyle 保持 ISO 的 Summarized；
- **粗糙度 Ra 数值表**：ToleranceValue 未改，按需在界面中选取。
