# Diagrams

Nine diagrams, one per idea that prose carries badly. All nine are in place and referenced from the guides.

They were generated from the prompts in [PROMPTS.md](PROMPTS.md) and are **deliberately label-free** — text rendering is the least reliable part of an image model, so the labelling is carried by the markdown caption beneath each image instead. That works, but it is a workaround, not the end state.

## Status

| # | File | State |
|---|---|---|
| 1 | `diagram-01-rotation-vs-translation.png` | Good |
| 2 | `diagram-02-orbit-heights.png` | Rings read flat — the ellipses pass through the statue with no occlusion |
| 3 | `diagram-03-wide-medium-detail.png` | Good |
| 4 | `diagram-04-turning-a-corner.png` | Middle cone does not visibly land on both walls, which is the point of the diagram |
| 5 | `diagram-05-connected-vs-isolated.png` | Good |
| 6 | `diagram-06-walking-vs-camera.png` | Good |
| 7 | `diagram-07-room-path.png` | Good |
| 8 | `diagram-08-vertical-bands.png` | All three wedges radiate from one camera position — see below |
| 9 | `diagram-09-ceiling-lanes.png` | Lane structure correct, but arrowhead directions contradict each other |

## Known issues, for a later pass

**The camera symbol is not consistent across the set.** Diagrams 4, 7 and 9 came from a second round that pinned the glyph explicitly and share one symbol. The other six each use a different one — plain rectangles, a lens-and-body icon, a video camera, a wall-mounted unit. The camera is the only element appearing in all nine, so this is the most visible inconsistency.

**Diagram 8 contradicts the text beside it.** It shows three coverage wedges fanning from a single fixed camera position. A diagram of one vantage point fanning three ways illustrates tilting from a fixed spot, which is precisely what diagram 9 and the surrounding text warn against. The wedges should originate from three positions along a route. This is an error in the prompt, not in the generation.

**Diagram 9's arrowheads disagree.** The path is one continuous route, so travel must flow consistently — down lane one, up lane two, down lane three, up lane four. Two lanes currently carry arrowheads pointing both ways. Separately, the upward-tilt chevrons and the travel arrows render as the same mark, so the two meanings are indistinguishable.

**Diagram 2's rings have no depth.** The orbit ellipses cross the statue without occlusion, so they read as flat bands rather than rings encircling it.

## The end state

Redrawing the set as SVG resolves all of the above at once, and none of it reliably survives another generation round. It also buys real text for the labels, `currentColor` strokes so the diagrams stay legible in both GitHub themes, and scaling that holds up in a printed handout.

The brief for each diagram — what it must show — is preserved in [PROMPTS.md](PROMPTS.md), which stays useful as the specification whether the next version is generated or drawn.

## Format notes

Current files are PNG, around 1600px on the long edge, quantised to a 64-colour palette. That covers a GitHub column at 2× and A4 at 300dpi. Aspect ratios are 16:9 for 1, 3, 5, 6, 8 and 9; 4:3 for 2 and 7; 1:1 for 4.
