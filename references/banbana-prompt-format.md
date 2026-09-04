# Banbana Prompt Format

Use this format when `SKILL.md` detects a clear request to replace, convert, rewrite, or output a prompt in Banbana format. A fixed trigger sentence is not required.

## Output Contract

- Output only one continuous Chinese natural-language paragraph. Do not add a scheme name, field label, explanation, code block, or closing remark.
- Begin with this sentence pattern: `这是一幅极其精致的商业产品[3D渲染/摄影]作品，专注于展现“[品牌或品类定位]”的品牌概念。`
- Continue in this order: photography or rendering method; placement and scale of the referenced product; composition and product hierarchy; environment, furniture, and props; camera angle and depth; physical support and contact shadows; lighting, materials, color, atmosphere, and finish.
- Describe only the visual result. Omit the campaign theme, main title, slogan, offer copy, event time, text-layout instructions, and every negative-requirement section.
- Do not output negative-keyword strings or exclusion lists. Convert any essential restriction into a positive visual state. Examples: `产品没有水珠` becomes `图1的产品表面干爽洁净`; `不要漂浮` becomes `图1的产品由稳定曲面承托并形成可信的接触阴影`; `不改变包装` becomes `保持图1的产品原有颜色、材质、结构与标签层级`.
- Preserve concrete visual facts supplied by the user, including aspect ratio, product count, scale, placement logic, camera angle, material behavior, and lighting. Do not invent campaign copy, dates, claims, or products.
- Apply Product Reference Binding to every product entity. Apply Image2 Wording Sanitization to the paragraph even though the negative-requirement field is absent.
- If multiple Banbana directions are requested, output one continuous paragraph per direction and separate paragraphs with `---`; do not add direction headings unless the user explicitly requests names.

## Compact Template

这是一幅极其精致的商业产品[3D渲染/摄影]作品，专注于展现“[品牌或品类定位]”的品牌概念。图像采用[摄影或渲染方法]，将图1的[产品或产品合集]置入[核心场景]，[产品占比、构图方向、主次层级与前后关系]。[环境、家具、道具与空间关系]。[镜头角度、景别、纵深、承托方式与接触阴影]。[主光、补光、材质细节、主辅色、空气感与整体质感]。

## Worked Example

这是一幅极其精致的商业产品3D渲染作品，专注于展现“年轻高端香氛生活”的品牌概念。图像采用近距离商业产品摄影技术，将图1的西兰六款产品合集放大置入时尚艺术客厅，整体外接范围约占画面宽度90%、高度70%，以斜向自由聚合形成高低错落、前后穿插、朝向丰富的大比例近景；图1的主要香氛产品靠近镜头成为视觉焦点，图1的其余产品沿斜向视线自然穿插，每款图1的产品各出现一次，品牌标识与核心标签清晰完整。空间由天空蓝弧形沙发、珊瑚粉圆鼓形脚凳、青柠绿雕塑边几与奶油白墙面组成，圆润家具近距离裁入画面，以大块曲面环抱图1的产品，同时呈现真实软包织物、沙发接缝与桌沿细节。镜头略微俯视并轻度倾斜，以前景曲线桌沿、中央图1的产品和后景弧形沙发形成紧凑纵深；图1的封闭式罐装产品在稳定曲面承托下以10°—20°轻斜，图1的藤条香薰瓶保持直立并完整呈现藤条，所有图1的产品均形成可信接触点与自然阴影。明亮侧窗日光结合正面柔光，细腻展现图1的棕色玻璃瓶渐变透光、图1的透明盒体真实折射与图1的香氛罐表面质感，保持图1的产品原有颜色、材质、结构与标签层级，画面呈现天空蓝、珊瑚粉、青柠绿和奶油白的鲜亮撞色，整体清爽透亮、干净通透，图1的产品表面干爽洁净。
