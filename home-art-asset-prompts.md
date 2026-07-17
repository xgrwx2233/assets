# 家长端首页美术生成提示词包

## 生产规则

每次请求只生成一个文件：不要请求一组、图集、多个状态、多个图标或整张 App 页面。

透明素材首选原生 RGBA PNG (`background=transparent`, PNG)，下载后检查 Alpha。若只能使用 ChatGPT 对话界面，请把“原生透明”段替换为纯 `#00FFFF` 色键背景段，下载后再抠成 Alpha；素材本体不得含青色。

**透明硬约束：**

```text
Output a PNG with a real native alpha channel. The transparent area must contain
no checkerboard pixels, white matte, background colors, or visible halo.
```

**对话界面色键替代：**

```text
Use a perfectly flat solid #00FFFF chroma-key background for later removal.
Do not use cyan anywhere in the asset. No texture, gradient, shadow, reflection,
or lighting variation may appear in the background.
```

**全局插画风格：**

```text
Premium semi-flat children's picture-book illustration for a family learning app;
soft gentle gradients, clean controlled outlines, warm daylight, natural green,
sky blue, cream white and warm yellow palette. Calm, encouraging, polished.
Avoid 3D game renders, anime, preschool sticker style, heavy outlines,
photorealism, text, logos, watermarks, UI mockups, borders, and frames.
```

## A01 首页背景（从两种方向中选一个）

文件 `home_bg_nature.png`，`750 x 1624`，刻意不透明：

```text
Use case: illustration-story
Asset type: full-screen mobile app background, opaque PNG, 750 by 1624 portrait.
Primary request: a quiet natural companion scene for a class-pet growth app.
Scene/backdrop: pale sky-blue upper area, a very soft sunlit glow, small leaves
and flowers only along the far top and bottom edges, low-contrast meadow tones
near the bottom. Leave the central 58 percent of the canvas calm, very light,
and almost empty for cards and text.
Style: premium semi-flat children's picture-book illustration; soft gradients,
clean outlines, warm daylight, natural green, sky blue, cream white and warm
yellow palette.
Constraints: no focal character, pet, house, foreground object in the center,
text, logo, button, card, frame, checkerboard, watermark, or UI screenshot.
```

可选家庭方向，文件 `home_bg_family.png`，`750 x 1624`，刻意不透明：

```text
Use case: illustration-story
Asset type: full-screen mobile app background, opaque PNG, 750 by 1624 portrait.
Primary request: a warm family-learning reading-corner background.
Scene/backdrop: softly sunlit window, blurred pale bookcase, and a small green
plant only near outer upper and lower edges. Centre is bright cream white and
deliberately empty for app cards.
Style: refined semi-flat children's picture-book illustration, calm and warm.
Constraints: extremely low-contrast scenery; no people, pet, readable book cover,
text, button, card, logo, watermark, checkerboard, or phone UI.
```

## A02 宠物展示台（不含宠物）

文件 `pet_stage_garden.png`，`1024 x 768`，透明 PNG：

```text
Use case: stylized-concept
Asset type: transparent decorative stage behind a separate pet character on a
mobile home screen, 1024 by 768 PNG.
Primary request: exactly one small rounded grassy platform with a few tiny
leaves, two or three simple flowers, and a subtle warm center glow where a pet
can stand.
Composition: centered low platform; keep upper 60 percent empty for a separate
pet illustration. Do not include any character.
Style: premium semi-flat children's picture-book illustration; soft gradients,
clean edges, restrained detail.
Output a PNG with a real native alpha channel. The transparent area must contain
no checkerboard pixels, white matte, background colors, or visible halo.
Constraints: no pet, tree, scenery, ground outside the platform, cast shadow,
text, logo, frame, watermark, or cyan in the asset.
```

## F01 页面边缘装饰（每条提示词单独生成一次）

### `deco_leaf_sprig_01.png`，512 x 512

```text
Use case: stylized-concept
Asset type: one transparent corner decoration for a mobile learning app, 512 by
512 PNG. Primary request: exactly one graceful curved sprig with five fresh green
leaves and one tiny pale-yellow flower, designed for a page corner.
Composition: sprig occupies lower-left half; generous transparent padding; no
second sprig or other decoration.
Style: premium semi-flat children's picture-book illustration, refined, soft,
clean, warm, low contrast.
Output a PNG with a real native alpha channel. The transparent area must contain
no checkerboard pixels, white matte, background colors, or visible halo.
Constraints: no cyan, background, soil, pot, shadow, text, icon sheet,
watermark, or border.
```

### `deco_flower_01.png`，512 x 512

```text
Use case: stylized-concept
Asset type: one transparent page-edge flower decoration, 512 by 512 PNG.
Primary request: exactly one small five-petal cream-white flower with a warm
yellow center and two soft green leaves. Isolated and centered with generous
transparent padding; no duplicated flower or bouquet.
Style: premium semi-flat children's picture-book illustration, clean and refined.
Output a PNG with a real native alpha channel. The transparent area must contain
no checkerboard pixels, white matte, background colors, or visible halo.
Constraints: no cyan, background, soil, pot, shadow, text, watermark, border,
or sprite sheet.
```

### `deco_sprout_01.png`，512 x 512

```text
Use case: stylized-concept
Asset type: one transparent growth decoration, 512 by 512 PNG.
Primary request: exactly one tender green sprout with two rounded leaves and a
very short stem, a gentle symbol of growth. Isolated and centered with generous
transparent padding.
Style: premium semi-flat children's picture-book illustration, polished and calm.
Output a PNG with a real native alpha channel. The transparent area must contain
no checkerboard pixels, white matte, background colors, or visible halo.
Constraints: no cyan, soil, pot, face, background, shadow, text, watermark,
border, extra sprout, or sprite sheet.
```

## F02 光效（每条提示词单独生成一次）

### `fx_star_glint_01.png`，512 x 512

```text
Use case: stylized-concept
Asset type: one transparent UI accent, 512 by 512 PNG.
Primary request: exactly one four-point warm-yellow star glint, small and elegant,
with a soft but clean-edged center; it must work over dark and light UI.
Composition: isolated, centered, generous transparent padding.
Style: refined picture-book accent, not glitter clip art.
Output a PNG with a real native alpha channel. The transparent area must contain
no checkerboard pixels, white matte, background colors, or visible halo.
Constraints: no cyan, background, particle cluster, text, watermark, border, or
sprite sheet.
```

### `fx_soft_glow_01.png`，512 x 512

```text
Use case: stylized-concept
Asset type: one transparent soft-light accent, 512 by 512 PNG.
Primary request: exactly one subtle warm cream-yellow circular light bloom with
soft falloff, for placement behind an illustration. Isolated and centered; fade
naturally to fully transparent at the outer edge.
Output a PNG with a real native alpha channel. The transparent area must contain
no checkerboard pixels, white matte, background colors, or visible halo.
Constraints: no cyan, background rectangle, star, lens-flare streak, text,
watermark, border, or sprite sheet.
```

## 成长系统图标（每个文件单独生成）

使用下方模板，依次替换 `[SUBJECT]`。输出均为 `512 x 512` 透明 PNG：

```text
Use case: stylized-concept
Asset type: one transparent illustrated game UI symbol, 512 by 512 PNG.
Primary request: exactly one [SUBJECT].
Composition: one centered object only, readable at 48 by 48 pixels, generous
transparent padding, simple silhouette, no adjacent object.
Style: premium semi-flat children's picture-book illustration; soft gradient,
clean outline, warm and elegant, not generic emoji or low-age sticker.
Output a PNG with a real native alpha channel. The transparent area must contain
no checkerboard pixels, white matte, background colors, or visible halo.
Constraints: no cyan, background, shadow, text, number, letter, logo, watermark,
frame, border, duplicate, variation, or sprite sheet.
```

| 文件 | `[SUBJECT]` |
| --- | --- |
| `icon_energy_bean.png` | one plump light-green energy bean with a tiny leaf motif, no face |
| `icon_level_badge.png` | one small warm-yellow rounded level medallion, blank center with no letters or numbers |
| `icon_growth_star.png` | one warm-yellow five-point growth star, no face |
| `icon_growth_leaf.png` | one fresh green leaf with a short curved stem |
| `sticker_heart_01.png` | one small coral-pink heart with a subtle highlight |
| `sticker_crown_01.png` | one small warm-yellow rounded crown with three soft points |
| `badge_growth_01.png` | one round green-and-cream achievement badge with a simple sprout in its center, no text |

## 图标、卡片和按钮：不要使用 AI 生成

`home`、`more`、`arrow_down`、`arrow_right`、`lock`、`parent`、`check` 应作为 SVG/Figma 矢量图标制作：`24 x 24 viewBox`、`2 px` 圆角描边、`currentColor`、无栅格纹理、无文字。

以下内容是响应式功能组件，使用 Figma 或前端代码制作，不应生成 PNG：主成长卡片、成长标签胶囊、开始问答按钮的默认/点击/禁用态、家长评价卡片、学生切换胶囊、头像框。

| 组件 | 规格 |
| --- | --- |
| 主成长卡片 | `#FFFFFF`，88% 透明度，24 px 圆角，12 px 软阴影 `#80A9B01F`，支持纵向拉伸 |
| 成长标签 | 米白色胶囊，999 px 圆角，图标 + 可编辑文本，不烘焙文字 |
| 问答按钮/默认 | 绿色渐变 `#77C85A -> #4CA85A`，20 px 圆角，白色可编辑标签 |
| 问答按钮/点击 | `#43984E`，向下 1 px，阴影减弱 |
| 问答按钮/禁用 | `#B7D7AF`，55% 透明，无阴影 |
| 家长卡片 | `#F4F1FA`，20 px 圆角，低视觉权重，淡紫灰图标 |
| 学生切换器 | 72% 白色胶囊，头像槽 + 可编辑姓名/班级 + SVG 箭头 |

## 上线验收

1. 透明 PNG 必须 `hasAlpha: yes`，四角 Alpha 均为 `0`。
2. 放在黑、白、蓝、红背景及目标尺寸下检查边缘。
3. 拒绝任何多对象图集、重复物件、文字、水印、棋盘格、地面或投影。
4. 游戏引擎导入时保留 Alpha，不使用颜色键透明。
