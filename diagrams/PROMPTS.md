# Generation prompts

Prompts for producing the nine diagrams briefed in [README.md](README.md) with an image-generation model.

## Before you start

**Generate without text where you can.** Text rendering is the least reliable part of any image model, and every one of these diagrams depends on its labels being correct. Each prompt below ends with a `NO TEXT` variant line — use it, then set the labels yourself in a vector editor. The result is faster to produce and correct on the first pass.

**Keep the style block identical across all nine.** They are one set and should look like it. Paste the block below at the front of every prompt.

**Generate each one separately.** Asking for two panels inside one image already stretches these models; asking for several diagrams at once will not work.

**Expect rerolls on 1, 5 and 9.** They are the three that depend on a correct/incorrect contrast, and models tend to render both halves as correct.

**Set the aspect ratio explicitly.** Left to itself a model will letterbox or recompose the diagram to fill whatever canvas it defaults to, which on the paired-panel diagrams squeezes both panels into half the width they need. Every prompt below carries its ratio on the last line. Ratios are reliable across models; exact pixel dimensions are not, so control the shape and let resolution follow.

---

## Size and aspect ratio

| # | Diagram | Ratio | Why |
|---|---|---|---|
| 1 | Rotation vs translation | 16:9 | Two panels side by side |
| 2 | Three orbit heights | 4:3 | Tall subject, wide rings, labels to the right |
| 3 | Wide, medium, detail | 16:9 | Subject plus three frames in a row |
| 4 | Turning a corner | 1:1 | Top-down plan, roughly square footprint |
| 5 | Connected vs isolated | 16:9 | Two panels side by side |
| 6 | Walking vs camera direction | 16:9 | Long horizontal path |
| 7 | The room path | 4:3 | Top-down room plan plus legend |
| 8 | Three vertical bands | 16:9 | Wedges extending across a cross-section |
| 9 | Ceiling lanes | 16:9 | Two room plans side by side |

**Generate at the largest resolution the model offers**, then downscale. These diagrams carry fine detail — dotted sight lines in 1 and 6, diagonal hatching in 8 — that disappears first when a small render is scaled up. As a floor, 1536px on the long edge.

**Final size in the repo:** around 1600px on the long edge for raster, which covers both a GitHub column at 2× and an A4 handout at 300dpi. If you convert to SVG, as recommended below, pixel dimensions stop mattering — but the aspect ratio still governs how the diagram is composed, so set it at generation time regardless.

**Ratio syntax by model:** Midjourney takes `--ar 16:9` appended to the prompt. DALL·E 3 and ChatGPT take 1792×1024 for 16:9 and 1024×1024 for square, with no true 4:3 — use square and crop. Imagen and Gemini accept 16:9, 4:3 and 1:1 as presets. Flux and Stable Diffusion take arbitrary dimensions; keep each side a multiple of 64.

---

## Style block

Prepend this to every prompt:

> Flat 2D technical line diagram in the style of an instructional manual or engineering textbook. Pure vector look: clean uniform-weight black strokes on a plain white background, one single accent colour (warm orange) used only for the camera path and camera positions. No perspective rendering, no 3D shading, no gradients, no shadows, no textures, no photorealism. Simple geometric shapes only. Generous white space. Clean neutral sans-serif labels, small, set in black. Minimal, precise, uncluttered.

---

## 01 — Scanning Objects

### 1. Rotation vs translation

> Two panels side by side, separated by a thin vertical rule, each with a heading.
>
> Left panel, headed "ROTATION": a single camera icon at one fixed point, drawn as a small simple rectangle. Three translucent view cones fan out from that one point at three different angles, sweeping across a simple statue shape to its right. A small cross mark sits beneath the panel. Caption underneath: "One position. No parallax."
>
> Right panel, headed "TRANSLATION": three camera icons at three clearly separate positions along a gentle arc, each with a view cone converging on the same statue shape. A small tick mark sits beneath the panel. Caption underneath: "Three positions. Depth recoverable."
>
> In both panels, mark one specific point on the statue with a small filled dot, and draw fine dotted sight lines from each camera to that dot, so the reader can see the sight lines are near-identical on the left and clearly divergent on the right.
>
> NO TEXT variant: identical, but omit all headings and captions, leaving clear empty space where they would sit.
>
> Aspect ratio 16:9. Generate at the largest resolution available.

### 2. Three orbit heights

> A simple statue on a plinth, drawn in flat elevation, centred.
>
> Three horizontal orbit rings encircle it, drawn as flattened ellipses in the accent colour to suggest they lie in horizontal planes: one low near the base, one at the statue's mid-height, one above its head. Each ring carries four evenly spaced camera icons.
>
> Cameras on the low ring are angled upward, cameras on the middle ring point horizontally, cameras on the high ring are angled downward. Show each camera's angle with a short view cone.
>
> Label each ring to its right, on a leader line: "HIGH — angled down", "EYE LEVEL — horizontal", "LOW — angled up".
>
> NO TEXT variant: identical, with leader lines drawn but their labels omitted.
>
> Aspect ratio 4:3. Generate at the largest resolution available.

### 3. Wide, medium, detail

> A simple statue drawn in flat elevation on the left.
>
> To its right, three framing rectangles arranged in a row, each showing a progressively tighter crop of that same statue: the whole figure, then head and shoulders, then the face alone. Draw them as camera-viewfinder frames with corner brackets.
>
> Between frame one and frame two, and again between frame two and frame three, mark one visual feature that appears in both — a collar line, a shoulder edge — with a small circle in each frame and a fine dotted line linking the two circles.
>
> Beneath the row, a horizontal arrow running left to right through three labels: "WHOLE" then "REGION" then "DETAIL".
>
> NO TEXT variant: identical, with the linking dotted lines and circles kept but all labels omitted.
>
> Aspect ratio 16:9. Generate at the largest resolution available.

### 4. Turning a corner

> Top-down plan view. A building drawn as a simple rectangle occupying the lower right, so that two of its outside walls meet at a right-angled corner pointing toward the upper left.
>
> A smooth continuous curved path in the accent colour sweeps around the outside of that corner, well clear of the walls.
>
> Three camera icons sit on the path: one early, one at the midpoint directly off the corner, one late. Each has a translucent view cone. The first cone covers only the first wall. The middle cone is wide enough to cover both walls at once. The last cone covers only the second wall.
>
> Label the middle camera on a leader line: "Both faces in view".
>
> NO TEXT variant: identical, leader line drawn, label omitted.
>
> Aspect ratio 1:1. Generate at the largest resolution available.

### 5. Connected vs isolated views

> Two panels side by side, separated by a thin vertical rule, each with a heading.
>
> Left panel, headed "CONNECTED": twelve small filled dots in the accent colour arranged in a loose three-by-four grid, with thin straight lines drawn between every pair of neighbouring dots, including diagonals, so the dots form a dense connected web or mesh.
>
> Right panel, headed "ISOLATED": four small filled dots in the accent colour, widely and irregularly scattered across the panel with large empty space between them, and no connecting lines at all.
>
> Both panels are otherwise identical in size and framing. Caption beneath the left: "Every view shares features with its neighbours." Caption beneath the right: "Good images, no relationships."
>
> NO TEXT variant: identical, headings and captions omitted. The contrast must be carried entirely by the presence and absence of connecting lines.

---

## 02 — Scanning Environments
>
> Aspect ratio 16:9. Generate at the largest resolution available.

### 6. Walking direction vs camera direction

> Top-down plan view.
>
> A long straight horizontal arrow runs left to right across the lower third of the image, in the accent colour, labelled beneath: "WALKING DIRECTION".
>
> Four camera icons sit evenly spaced along that arrow. Every camera is angled consistently at about 45 degrees up and to the left — that is, backward relative to the direction of travel, not forward. Each has a short translucent view cone. Label the group above: "CAMERA DIRECTION".
>
> A single small filled dot sits in the upper left area, representing a fixed feature in the room. Draw fine dotted sight lines from each of the four cameras to that one dot, making clear that the angle to it changes substantially from the first camera to the last.
>
> NO TEXT variant: identical, all labels omitted, sight lines and cones kept.
>
> Aspect ratio 16:9. Generate at the largest resolution available.

### 7. The room path

> Top-down plan of a simple rectangular room, drawn as a clean outline with double-line walls. A door gap in the lower wall, a window marked in the upper wall, and one small rectangle in the middle right representing a table.
>
> Four overlaid paths, each in a different line style, all in the accent colour:
> a continuous solid loop following just inside the perimeter of the room;
> two dashed straight lines running corner to corner, crossing at the centre to form an X;
> one dotted straight line crossing the room's short axis;
> one small closed arc, like a single flower petal, curving around the table.
>
> A compact legend in the lower right corner outside the room outline, with a short sample of each line style: "Perimeter", "Diagonals", "Crossing", "Local arc".
>
> NO TEXT variant: identical, legend drawn as line samples in a box with the names omitted.
>
> Aspect ratio 4:3. Generate at the largest resolution available.

### 8. Three vertical bands

> Cross-section through a room, side view: a floor line, a ceiling line, and a wall at each side, forming a simple rectangle. Include a small hanging light fitting on the ceiling and a small piece of furniture on the floor for scale.
>
> A camera icon stands at the left, roughly at eye height. From it, three translucent wedges of coverage extend rightward across the room: an upper wedge angled up toward the ceiling, a middle wedge running horizontally, a lower wedge angled down toward the floor.
>
> The two zones where adjacent wedges overlap must be the visual emphasis of the image: fill them with fine diagonal hatching, noticeably denser than the wedges themselves, and mark each with a short leader line.
>
> Label the wedges at their right-hand ends: "UPPER", "MIDDLE", "LOWER". Label both hatched zones: "overlap".
>
> NO TEXT variant: identical, hatching and leader lines kept, all labels omitted.
>
> Aspect ratio 16:9. Generate at the largest resolution available.

### 9. Ceiling lanes

> Two panels side by side, separated by a thin vertical rule, each a top-down plan of the same simple rectangular room.
>
> Left panel, headed "LANES": one continuous serpentine path in the accent colour, boustrophedon, like mowing a lawn — up the left side, across, back down, across, up again — with arrowheads showing the direction of travel. Five camera icons spaced along the path, each marked with a small upward-pointing chevron to show consistent upward tilt. A tick mark beneath.
>
> Right panel, headed "STANDING STILL": a single camera icon at the centre of the room, with eight short view cones radiating outward from that one point in a full circle. No path, no travel. A cross mark beneath.
>
> Caption beneath the left: "Tilt while moving." Caption beneath the right: "Tilting instead of moving."
>
> NO TEXT variant: identical, headings and captions omitted.
>
> Aspect ratio 16:9. Generate at the largest resolution available.

---

## Afterwards

Convert the results to SVG before committing, so the diagrams scale and stay legible in a printed handout. If the model returns raster only, trace it or redraw over it — nine diagrams of this simplicity are quick to rebuild as vectors, and rebuilding is usually faster than fighting a model toward exact geometry.

Set labels as real text rather than outlines, and set strokes and text in `currentColor` where possible, so the diagrams stay readable against both light and dark backgrounds on GitHub.
