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

## Camera glyph

Paste this after the style block, on every prompt that contains a camera.

The first round came back with a different camera symbol in almost every image — plain rectangles, a lens-and-body icon, a video camera, a wall-mounted CCTV unit, a photo camera. Individually fine, but the camera is the one symbol that appears in all nine, so the set did not cohere. Pin it explicitly:

> Every camera in the image is drawn as the same simple symbol: a small horizontal rectangle outlined in the accent colour, with a short trapezoid lens stub projecting from one side to show which way it faces. No round lens, no viewfinder bump, no body detail, no wall bracket, no tripod. Every camera in the image uses this identical symbol at the same size.

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

> Top-down plan view, drawn entirely within the frame with a clear margin on all four sides. Nothing runs off the edge of the image.
>
> A building occupying the lower right, drawn as a closed rectangle with its interior filled with fine even diagonal hatching so that it reads as solid mass. Two of its outside walls meet at a right-angled corner pointing toward the upper left. The building must be a complete closed shape, not two open lines.
>
> One smooth continuous curved path in the accent colour sweeps around the outside of that corner at a constant clearance from both walls. Both ends of the path stop inside the frame, with visible empty space beyond each end.
>
> Three cameras sit on the path: one near the start, one at the midpoint directly off the corner, one near the end. Each casts a pale translucent view cone. The first cone falls only on the first wall. The middle cone is wide enough to span the corner and cover both walls at once. The third cone falls only on the second wall. The three cones must not overlap one another.
>
> A short leader line runs from the middle camera out into empty space and stops.
>
> NO TEXT anywhere in the image.
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

> Top-down plan of a simple rectangular room, drawn as a clean outline with double-line walls. A door gap in the lower wall, a window marked in the upper wall, and one small rectangle representing a table in the lower right quadrant.
>
> Four paths overlaid inside the room, all in the accent colour, each in a clearly different line style:
>
> 1. a SOLID continuous loop running just inside the perimeter;
> 2. two LONG-DASHED straight lines corner to corner, crossing at the centre to form an X;
> 3. one DASH-DOT straight line running from the top wall to the bottom wall, placed in the left half of the room so that it comes nowhere near the table;
> 4. one FINE-DOTTED closed loop, shaped like a single flower petal, curving around the table.
>
> The four line styles must be distinguishable from each other at a glance. No path crosses a wall or extends beyond the room. Nothing passes through the table except the petal loop that encircles it.
>
> A legend box in the lower right corner, outside the room outline, holding four short horizontal samples of the four line styles in order, with empty space where their names would go.
>
> NO TEXT anywhere in the image.
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

> Two panels side by side, separated by a thin vertical rule. Each panel holds an identical top-down plan of the same simple rectangular room, drawn with double-line walls, a window in the top wall and a door gap at the lower right.
>
> Left panel: ONE single continuous unbroken path in the accent colour, in a strict boustrophedon pattern — exactly the route a lawnmower takes. Precisely four straight vertical lanes, evenly spaced across the width of the room, joined at alternating ends by short semicircular 180-degree turns: the bottom of lane one to the bottom of lane two, the top of lane two to the top of lane three, the bottom of lane three to the bottom of lane four. The path must never cross itself, never branch, and never break anywhere along its length. Small arrowheads at intervals show one consistent direction of travel. Four cameras spaced along the lanes, each with a small chevron directly above it pointing upward. A large tick mark centred beneath the room.
>
> Right panel: one camera at the exact centre of the room, with eight short dashed arrows radiating outward from it in a full circle. No path, no travel, no second camera. A large cross mark centred beneath the room.
>
> NO TEXT anywhere in the image.
>
> Aspect ratio 16:9. Generate at the largest resolution available.

---

## Afterwards

Convert the results to SVG before committing, so the diagrams scale and stay legible in a printed handout. If the model returns raster only, trace it or redraw over it — nine diagrams of this simplicity are quick to rebuild as vectors, and rebuilding is usually faster than fighting a model toward exact geometry.

Set labels as real text rather than outlines, and set strokes and text in `currentColor` where possible, so the diagrams stay readable against both light and dark backgrounds on GitHub.
