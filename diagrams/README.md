# Diagrams

The scanning guides mark nine places where a diagram carries the idea better than prose. Each is flagged in the source with an HTML comment:

```
<!-- DIAGRAM: <what it needs to show> -->
```

Until they are drawn, those comments are invisible to a reader and the guides read as continuous prose. Nothing is broken by their absence; the text stands on its own.

## Brief

All nine explain the same underlying thing — that reconstruction depends on seeing surfaces repeatedly from different positions — so they should read as one set. Plain line work, no perspective rendering, legible at a page width and in a printed handout.

### 01 — Scanning Objects

1. **Rotation vs translation.** A fixed camera sweeping its view across a subject, beside a camera at three positions along a path all pointing at that subject. The contrast is the point: the first produces no feature displacement, the second does.
2. **Three orbit heights.** Low, eye and high rings around a statue, camera angled up, level and down respectively, showing what vertical coverage each contributes.
3. **Wide, medium, detail.** Three nested framings on one subject, with shared features marked between each pair to show the chain that connects a close-up back to the whole.
4. **Turning a corner.** A camera path curving around a building corner, with three sample frames showing both façades in view through the turn.
5. **Connected vs isolated views.** A dense grid of camera positions with overlapping sightlines, against four scattered positions with none. The failure case is as important as the good one.

### 02 — Scanning Environments

6. **Walking direction vs camera direction.** A straight path left to right, camera arrows angled consistently back at about 45°, showing how a fixed feature travels across successive frames.
7. **The room path.** A room plan layering perimeter loop, both diagonals, a central crossing, and a small arc around one piece of furniture.
8. **Three vertical bands.** A room cross-section with upper, middle and lower view bands, drawing attention to the overlap margins between them rather than the bands themselves.
9. **Ceiling lanes.** A room plan with serpentine lane paths and consistent upward tilt, set against a single stationary point radiating tilt directions.

## Format

SVG, committed here, referenced from the guides by relative path. Text in the diagram should be real text rather than outlines, so it stays searchable and legible when scaled.

Both light and dark backgrounds are worth accounting for: strokes and labels set in `currentColor`, or a pair of files, so the diagrams remain readable in whichever theme the reader is using on GitHub.
