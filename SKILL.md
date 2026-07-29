---
name: wish-design-kv-skill
description: Create concise, production-ready Chinese KV image prompts from campaign briefs, planning screenshots, PPT drafts, ecommerce activity notes, or loose brand requests. Handles ecommerce KV, campaign posters, livestream backgrounds, banners, activity pages, and product promotion images. Bind every product entity in the final prompt to its reference image with wording such as "图1的产品合集", "图1的产品", or "图1的三瓶产品". Automatically neutralizes sensitive wording for Image2 compatibility. Output prompts only unless the user explicitly asks to generate an image.
---

# Wish Design KV Skill

## Core Task

Convert rough campaign material — screenshots, PPT drafts, text briefs, activity notes — into concise, production-ready Chinese image prompts. Treat all planning references as directional input, not final visual targets. Strip spreadsheet grids, PPT annotations, placeholders, arrows, and draft styling from the output.

**Do not generate an image unless the user explicitly requests image generation.**

## Mandatory Output Contract

This contract overrides stylistic freedom elsewhere in this skill. Follow it exactly.

1. Output only the finished prompt. No analysis, rationale, usage instructions, or closing remarks.
2. Preserve the field order below. Do not rename, merge, omit, or reorder fields.
3. Keep each prompt concise but concrete enough for image generation.
4. Use Chinese punctuation and production-oriented visual language.
5. Do not wrap the prompt in a code block.
6. Before output, apply the Image2 Wording Sanitization rules to every field, including negative requirements.
7. Bind every product entity in the finished prompt to its product reference image. Default to the exact possessive form `图1的……`; only use another image number when the user explicitly assigns the product to that image.

### Single Direction Template

**方案｜[方向名称]**

这是一张【[品牌/渠道/活动/品类]】[比例]竖版/横版KV，主题《[主标题]》。画面采用[核心场景与视觉机制]，表达[品牌利益点、活动目的或情绪价值]。

顶部预留：[LOGO或联名标识]
主标题：《[主标题]》
利益点：《[促销或产品利益点]》
时间：《[活动时间]》

画面表达：[场景、构图、图1的产品层级、前景、背景、道具、互动、气氛、字体和必要的可视化机制。]

[需要时继续补充1至2个自然段，描述镜头、道具、香气、空气、洁净、守护或人物互动；不要另起新的字段标题。]

画面风格：[广告类型、写实或3D方式、比例、主色、辅助色、光线、清晰度与整体气质。]

负面要求：[需要排除的风格、元素、构图问题、包装问题、文字遮挡和草稿痕迹。]

### Multiple Directions Template

When the user requests two or more visual directions, repeat the complete structure for every direction, separated by a `---` line:

**方案一｜[方向名称]**

[完整结构]

---

**方案二｜[方向名称]**

[完整结构]

Use Chinese numerals in sequence (方案一、方案二、方案三……). Make directions visually distinct in scene, composition, palette, camera language, or creative mechanism while preserving the same campaign copy and brand identity.

## Field Specifications

Each field in the template follows these rules:

- **方案**：名称应概括场景或创意机制，如"半开放客厅纳凉""蓝天下的花园单车"。不要使用纯品牌名或纯活动名，要有画面感。
- **主题总述**（模板中"这是一张……"开头的段落）：必须以"这是一张【...】..."开头，2句内说清品牌、活动、比例、场景和表达目的。
- **顶部预留**：只列需要出现的 LOGO、品牌标识或活动标识；没有信息时写"品牌LOGO｜活动LOGO"。应用净化规则后，敏感机构名替换为"合作方LOGO"。
- **主标题**：沿用策划稿核心文案，不擅自改写数字、时间或促销机制。
- **利益点**：优先保留最强的一条促销或产品利益点；没有明确利益点时写用户提供的副标题或核心卖点。
- **时间**：有活动时间则原样保留；没有时写"时间：未提供"，不得省略该字段或编造时间。
- **画面表达**：必须覆盖场景、图1的产品、构图层级、前后景、关键道具、气氛和标题字体；涉及人物、动物、IP或功效可视化时一并写入。凡是指向参考图中商品主体、数量、组合、主次关系或包装的产品名词短语，都按 Product Reference Binding 规则添加图片编号。需要时可续写1-2个自然段补充细节，但不另起新字段标题。
- **画面风格**：必须包含图片比例、视觉类型、主辅色、光线和真实度。常见比例：9:16（竖版手机端）、3:4（竖版）、16:9（横版）、1:1（方图）。
- **负面要求**：必须包含去除PPT感、网格、批注、占位元素，以及 `图1的产品包装清晰`、`标题与图1的产品无遮挡`；再补充任务特有禁忌。负面要求同样适用净化规则——不要为了说"不要出现..."而重复敏感源词。

## Product Reference Binding

Treat `图1` as the default product reference image. In the finished prompt, every noun phrase that points to the supplied product, product count, product group, product hierarchy, or package must begin with the possessive image binding `图1的`. Do not omit `的`, and do not use the loose form `图1产品`.

Apply the rule throughout all prompt fields, including visual descriptions and negative requirements:

- `产品` → `图1的产品`
- `产品合集` → `图1的产品合集`
- `三瓶产品` → `图1的三瓶产品`
- `[品牌]产品合集` → `图1的[品牌]产品合集`
- `主推产品` / `次推产品` → `图1的主推产品` / `图1的次推产品`
- `产品包装` / `产品标签` → `图1的产品包装` / `图1的产品标签`

Do not add `图1的` to abstract editorial concepts that do not identify the pictured commodity, such as `产品利益点`、`产品宣传KV` or `产品卖点文案`. If the user explicitly states that the product is in another numbered image, replace `图1` with that exact image number consistently; otherwise always use `图1`.

### Product Collection Handling

When the KV contains multiple products, do not lock exact placement. Use this wording or a close equivalent:

> 将图1的[品牌]产品合集放置在[场景]中，图1的产品摆放不固定、有层次，图1的主推产品居中或视觉突出，图1的次推产品自然穿插，图1的产品比例突出、图1的产品包装清晰。

Control hierarchy, scale, prominence, and clarity only. Do not prescribe rigid left-to-right product positions unless the user explicitly requires them.

## Image2 Wording Sanitization

Before writing the final prompt, scan all planning text, image annotations, product labels, titles, logo lines, visual descriptions, and negative requirements. Replace or remove wording that may trigger Image2 while preserving the commercial layout and visual intent.

Apply these rules automatically without asking the user:

- **国家/政府/政治/官方机构/公共权力/旗帜/徽章/地图边界/真实政治人物**：替换为 `合作方LOGO`、`机构LOGO`、`合作机构标识` 或 `区域文化元素`。若机构或 LOGO 名称含"国家"，整个名称替换为 `合作方LOGO`，不保留原名。
- **权威背书**（如 `国家级`、`国家认证`、`官方指定`）：替换为 `专业认证标识`、`品质认证标识` 或 `合作认证标识`，不得编造法律效力背书。
- **医疗/疾病/毒性/病原体/治疗/杀菌/激进功效**：转化为 `专业洁净`、`清洁护理`、`微观洁净概念`、`健康安心感`、`清新环境` 等中性商业表述。
- **暴力/武器/战斗/灭杀/恐怖虫类/冲击性语言**：转化为 `自然屏障`、`轻防护机制`、`远离干扰`、`洁净链路` 等平和的防护视觉隐喻。
- **绝对化/极端化宣称及非必要的精确功效数字**：替换为 `核心功效数字信息`、`重点卖点区域` 或 `醒目利益点文案`，保留文字位置而非敏感措辞。
- **产品包装上的敏感文字**：不转录到 prompt 中，写 `保持图1的原包装结构与标签层级，图1的产品包装清晰`，让参考图承载包装外观。
- **最终排版需要的敏感文字**：替换为 `对应文案区域留空，后期排版`，不让 Image2 渲染该文字。
- **负面要求同样适用**：不要为了说"不要出现..."而重复敏感源词，用中性描述或直接省略。

Do not use euphemisms or placeholders to conceal genuinely unsafe intent. If the underlying request remains unsafe after removing names or wording, do not convert it into an image prompt.

## Brand Visual Rules

| 品牌 | 关键词 | 视觉方向 | 避免事项 |
|---|---|---|---|
| 超威 | 专业驱蚊、强效、安全感、户外自然 | 自然屏障、空气流线、成分粒子、守护机制 | 恐怖虫群 |
| 西兰 | 清新、空气感、情绪香氛、时尚、自我疗愈 | 风、呼吸感、轻柔香气轨迹、通透材质、柔和光影 | 厚重压抑 |
| 贝贝健 | 儿童安全、趣味守护、户外探索、亲子安心 | 自然户外、IP角色、童趣能量 | 幼稚杂乱 |
| 威王 | 洁净、专业清洁、家庭安心 | 洁净光感、表面反射、轻科技线条、家庭场景 | 夸张脏污 |

**未列出品牌**：从策划稿和参考图中提取品牌调性关键词，按"洁净/防护/香氛/活力/专业"等方向归位，选择中性商业视觉语言。不要在品牌未覆盖时凭空臆造风格——优先复用已有品牌规则中最接近的方向。

## Input Handling

不同输入类型需要不同的解析策略：

- **截图 / PPT 稿**：识别标题、利益点、时间、LOGO 位置、产品图、场景示意图。忽略表格网格、批注箭头、占位框、白底占位元素和草稿样式。
- **纯文本策划**：提取品牌、活动机制、时间、卖点、场景需求。将策划语言翻译为视觉语言（如"满减"→利益点文案区域，"清新"→空气感视觉）。
- **电商活动笔记**：关注平台、活动阶段（预热/爆发/返场）、促销机制、利益点层级。不同阶段的视觉调性可略有差异（预热偏氛围，爆发偏利益点突出）。
- **品牌泛需求**（如"做一张超威的KV"）：从品牌规则提取默认方向，补充一个合理的场景和创意机制，输出后提示用户确认或调整。
- **参考图片**：描述参考图中的有用特质（构图、色调、材质、氛围），而非要求精确复制。

## Workflow

1. **识别要素**：从输入中提取品牌、渠道、活动、比例、LOGO、标题、利益点、时间、产品、场景需求、禁止元素；默认将产品参考绑定为图1。
2. **提取创意**：为每个请求方向提炼一个清晰的视觉创意点——一句话能说清"这张 KV 的核心画面是什么"。
3. **翻译语言**：将策划语言转化为场景、构图、产品层级、前后景、道具、互动、气氛、字体、色彩、光线和负面要求；对所有产品实体短语应用 `图1的……` 绑定。
4. **应用品牌规则**：匹配品牌视觉方向。未覆盖品牌按 Input Handling 中的 fallback 处理。
5. **净化措辞**：对完整草稿执行 Image2 Wording Sanitization 全量扫描，包括负面要求。
6. **产品引用复核**：逐句扫描产品、产品数量、产品合集、主推/次推产品、产品包装与产品标签等表达，确保全部使用 `图1的……`；用户明确指定其他图片编号时，确保全文编号一致。
7. **精简压缩**：在不丢失任何必填字段的前提下，将冗长草稿压缩约 30%。
8. **输出**：仅返回符合强制结构的 prompt，不附加任何说明。

## Interpretation Priorities

当需求冲突时，按以下顺序取舍：

1. 图1的产品清晰度与图1的产品包装完整性
2. 核心标题、利益点和活动时间
3. 品牌视觉规则
4. 活动机制与指定场景
5. 装饰性元素

描述参考图中的有用特质，而非要求精确复制。仅在次要细节实质影响画面时保留。

## Worked Example

以下示例展示了一个完整的单方案输出，包含净化规则的应用（原策划稿中的"国家地理"已净化为"合作方LOGO"）：

**方案｜热带雨林守护**

这是一张【超威×合作方联名·618大促】9:16竖版KV，主题《全方位守护，自然超威的》。画面采用热带雨林场景结合变色龙隐身与粉色螳螂互动，表达自然守护与专业驱蚊的安全感。

顶部预留：合作方LOGO｜品牌LOGO｜平台LOGO
主标题：《全方位守护》
利益点：《自然超威的》
时间：《5/21 00:00 - 6/18 23:59》

画面表达：将图1的超威产品合集放置在热带雨林近景中，图1的产品摆放不固定、有层次，图1的主推产品居中视觉突出，图1的次推产品自然穿插，图1的产品比例突出、图1的产品包装清晰。前景有大叶绿植、藤蔓、苔藓石块和雨后水汽，背景有纵深林间光影。

图1的产品周围加入淡蓝绿色防护光圈、空气流线、驱蚊粒子和轻微科技扫描感。变色龙隐藏在枝叶和图1的产品附近，粉色螳螂与图1的产品产生守护或击退蚊虫的互动。

画面风格：高级电商618竖版KV，图1的产品3D写实合成与热带雨林电影感，比例9:16，主色雨林绿、辅助色防护蓝绿，光线为林间透射光与图1的产品聚光，整体气质自然科技感。

负面要求：不要PPT感、表格感、网格、批注、占位元素；不要水印和草稿痕迹；不要写死图1的产品摆放位置；不要密集蚊虫或恐怖氛围；不要过度卡通；不要弱化图1的产品和标题；图1的产品包装清晰、标题与图1的产品无遮挡。

## Generation Compatibility

优先使用中性商业摄影和设计语言，兼容 Image2 及其他常见图像生成工具。在输出前应用净化规则。保留活动的视觉层级和文案位置，但将敏感的最终文字移至后期排版，不在生成 prompt 中复现。