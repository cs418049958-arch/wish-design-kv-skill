# PDP Planning Screenshot to Image2 Prompt

Use this contract only for ecommerce PDP/detail-page screens. It overrides the KV field order, `方案｜方向名称` wrapper, `顶部预留/主标题/利益点/时间` fields, and multiple-direction format. Keep all other global rules from `SKILL.md`, especially product-reference binding and Image2 wording compatibility.

## Output Contract

1. Output only one finished Chinese prompt. Do not add analysis, rationale, usage instructions, greetings, closing remarks, or a code fence.
2. Start with `生成一张……中文电商详情页单屏成品` and state the canvas size or ratio, screen purpose, rendering method, and overall visual language.
3. Organize the prompt with compact semantic sections. Use only sections that the screen needs, normally:
   - `【整体风格】`
   - `【顶部标题】`
   - `【主体构图】`
   - one section for each content module or scene
   - `【排版与限制】`
   - `避免：……`
4. Default to a concise production version: preserve all required information while removing repeated adjectives and duplicated constraints. Aim for roughly half the length of an exhaustive prompt. Expand only when the user explicitly asks for a highly detailed version.

## Reverse-Engineering Workflow

1. Separate the actual page from planning notes, grids, reference pictures, arrows, grey placeholders, crop borders and spreadsheet/PPT artifacts.
2. Read the screen in visual order. Recover the intended title, subtitle, exact copy, data, units, footnote numbers, module hierarchy, scene requirements, product placement, evidence material and exclusions.
3. Merge off-canvas planning notes into the finished composition. Convert every placeholder such as `场景图`、`产品图`、`报告` or grey box into a concrete final visual description.
4. Rebuild the complete page, not the draft. Specify canvas ratio, safe margins, vertical section proportions, alignment, relative scale, foreground/midground/background, overlaps, callout lines and reading order.
5. Describe each required scene concretely: location, object, action, state, camera angle, lighting, material, cleanliness level, atmosphere and visualized mechanism. For people, state approximate identity, pose, interaction and natural anatomy. For diagrams, state structure, labels and leader-line mapping.
6. Preserve source business text, numbers, labels, units, hierarchy, direction and footnote markers. Do not invent subtitles, conclusions, metrics, institutions, certifications or commercial claims. Do not strengthen a claim beyond the planning draft.
7. When the planning draft supplies reports or certificates, describe their placement and document texture. Remove watermarks and blur institution names, report numbers and sensitive identifiers unless the user supplies approved readable text.
8. Apply Product Reference Binding to every pictured product entity. If a product reference is supplied, require exact preservation of bottle shape, cap or trigger, label hierarchy, colors, proportions, pack count and main/secondary relationship. Do not redesign the package.
9. End with task-specific negative requirements covering layout failures, omitted modules, wrong scene substitutions, text errors, deformed products or hands, unwanted draft artifacts and unauthorized additions.

## Text and Compatibility Rules

- Keep user-supplied ordinary PDP copy, measurements, data and superscript footnote numbers verbatim when they are required on the finished screen. Never fabricate missing values.
- If wording is genuinely incompatible with Image2 or unsafe, apply the global sanitization rules without hiding unsafe intent. Prefer neutral visual wording or reserve the text area for later typesetting.
- Do not copy claims, percentages, brands, watermarks or sample English from a visual reference unless the planning draft explicitly designates them as final source content.
- Require accurate, readable Chinese with no garbling. Keep headings, labels and data unobstructed.

## Composition Pattern

Use this flexible pattern rather than a rigid form:

`生成一张[尺寸/比例]竖版中文电商详情页单屏成品，主题为“[本屏目的]”。采用[真实摄影/3D剖视/信息图/报告组合]，延续[品牌或相邻页面]的[主色、辅助色、字体与质感]。`

`【整体风格】[背景、色彩、字体、光线、圆角、阴影、真实度、完成度。]`

`【顶部标题】[准确标题、副标题、强调词颜色、上标和对齐。]`

`【主体构图】[页面分区比例、中央主体、场景位置、视觉路径和层级。]`

`【模块/场景名称】[具体环境、主体、动作、材质、可视化机制、标签和对应关系。]`

`【排版与限制】[必须保留的文字、数据、产品绑定、报告处理、不得增加的内容。]`

`避免：[乱码、PPT感、网格、批注、占位框、水印、错位、遮挡、场景替换、结构畸形、包装变形、额外文案与不符合品牌的视觉效果。]`

Do not add the KV-only fields `方案`、`顶部预留`、`利益点` or `时间` unless those fields are genuinely part of the PDP screen itself.
