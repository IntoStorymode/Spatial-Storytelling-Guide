# Scanning Environments

A room is not a large object. It is the case where you are standing inside the thing you are recording, and that inversion changes the method more than it first appears.

This guide assumes you have read the principle set out in [01 — Scanning Objects](01-scanning-objects.md): move the camera through space while repeatedly observing the same surfaces, because rotation on its own produces no parallax. All of that still holds. What follows is what changes when you are inside.

## Why the inversion matters

Around an object, good practice is close to automatic. You walk in a circle, the subject stays in frame, and every step gives you a new angle on the same surfaces. Coverage and parallax arrive together, almost for free.

Inside a room, they come apart. You can point the camera at every wall, ceiling and corner in the space and still produce something unusable — because seeing a surface is not the same as seeing it from several positions.

So the objective is not *film everything in the room once*. It is:

> Build overlapping coverage, so the same features are visible repeatedly from different camera positions.

The path has to be designed. It will not happen by walking about.

## Walking direction and camera direction are separate

This is the single most useful habit to acquire indoors, and it has no equivalent in object capture.

You can walk one way while looking another. Walking forwards along a wall while aiming the camera 45° back across the room means the features in frame sweep steadily across the field of view — which is exactly the displacement the solver needs. Walking forwards while looking forwards gives you much less: things ahead of you grow slowly larger and shift very little.

Treat *where you are*, *where you are looking*, and *what you have already seen from elsewhere* as three separate things to track.

<!-- DIAGRAM: walking direction as a straight arrow left to right, camera direction as a set of arrows angled consistently back at ~45°, showing the resulting displacement of a fixed feature across successive frames. -->

## Do not just walk the perimeter

Following the walls is the natural instinct and it is not enough on its own. A perimeter lap gives you one viewing angle on most of the room and a poor one on the middle.

A room wants a network of paths rather than a circuit:

- the perimeter
- diagonals, corner to corner
- straight across the middle, both ways
- sideways passes along important walls
- small arcs around significant objects
- upward and downward passes
- deliberate passes connecting one area to another

Think **perimeter plus diagonals plus crossings plus local loops**, not one lap.

Cross-room passes earn their place because they produce camera positions a perimeter lap simply cannot, and they give every wall and object a different background to be measured against.

<!-- DIAGRAM: room plan showing the layered path — perimeter loop, both diagonals, a central crossing, and a small arc around one piece of furniture. -->

## Start with a context pass

Walk slowly through and around the space with the camera roughly horizontal, establishing the overall geometry: the walls, how they meet, the major furniture, doors, windows, the architectural landmarks.

Two habits make this pass much more useful.

**Look diagonally across the room, not at the nearest wall.** Somewhere around 30–60° inward. A frame containing near furniture, the floor, a corner and the opposite wall ties four parts of the room together at once. A frame filled edge to edge with one wall ties nothing to anything.

**Keep several depths in shot.** Something near, something at middle distance, something far. Depth layering in a single frame is what lets the solver place those things relative to each other.

This pass is the framework every later pass connects into. It is worth doing carefully.

## Three vertical layers

Complete coverage of a room is best thought of as three overlapping horizontal bands, captured on separate passes over similar routes.

- **Middle.** Camera roughly level. Room geometry, walls, furniture, doors and windows.
- **Upper.** The same sort of route, looking diagonally upward. Upper walls, the wall–ceiling junction, ceiling, light fittings, beams.
- **Lower.** Again, looking diagonally downward. Lower walls, skirting, floor, the bases of furniture.

The important word is *overlapping*. Three separate datasets — a ceiling, a room and a floor with nothing in common — is a much worse outcome than three bands that share generous margins with their neighbours. Ceiling should connect to upper wall, upper wall to room, room to lower wall, lower wall to floor.

<!-- DIAGRAM: room cross-section with three horizontal view bands (upper, middle, lower), showing the overlap margins between adjacent bands as the connecting tissue. -->

## Ceilings and floors

Ceilings present the obvious temptation: stand still, tilt up, sweep around. That gives coverage and almost no parallax, for the reason set out at the start.

> Never tilt instead of moving. Tilt while moving.

Angle the camera up perhaps 30–60° and then *walk*. The same ceiling features get observed from a sequence of different positions, which is what makes them reconstructable.

Do not point straight up. A frame of nothing but ceiling has no relationship to the rest of the room. Start with the upper wall and the wall–ceiling junction in shot, then raise the angle if you need to. A frame with ceiling, top of wall, corner and a light fitting is worth several frames of blank plaster.

**Large plain ceilings are genuinely hard**, because even a moving camera finds nothing to track on them. Work from the anchors that exist — light fittings, beams, vents, sprinklers, pipes, coving, edges, joints, stains, changes in material — and keep them in overlapping view as you move.

For a big room, walk lanes rather than wandering. Up one side, back down the next, camera tilted up throughout, the way you would mow a lawn — except the surface is above you.

<!-- DIAGRAM: room plan with serpentine lane paths (up, across, back), camera tilt indicated as consistently upward, contrasted with a single stationary point radiating tilt directions. -->

Floors work identically. Tilt down and walk; hold an oblique angle rather than pointing straight down, so that skirting, furniture legs, thresholds, rugs and doors stay in frame and keep the floor tied to the room. The anchors are floorboards, tiles, joints, cables, rugs and material transitions.

## Turn gradually

When changing direction, do not spin. A sudden 90° rotation breaks the chain of shared features, and the two halves of the recording may end up unrelated.

Move through the corner instead: first wall, then corner with both walls visible, then second wall. The corner does the joining. This is the same logic as working around the outside of a building, applied from the inside.

## Treat important walls as objects

If a wall carries the content — artwork, shelving, windows, signage, anything the story rests on — give it its own pass.

Stand far enough back that some surrounding context stays in frame. Move sideways while keeping the wall in view, and collect face-on, left-oblique and right-oblique views of it. Do not stand still and pan across it.

## Detail without disconnection

For an object in the room that needs more resolution — a fireplace, a desk, a bookshelf, a particular photograph — switch briefly back into object-capture behaviour. Small arcs rather than a straight approach: come in, arc one way, back off, come in again from another direction, arc the other way.

The failure to avoid is the same one as in object capture, and it is easier to commit indoors: going from a wide shot to a frame entirely filled by one object, then back out. Nothing in that close frame locates it. Work through intermediate views — wide, medium, closer, medium from another angle, wide again — and keep some context at the closest range: a table edge, the surrounding wall, the floor beneath.

## Connection passes

This is the failure that most often survives an otherwise careful session.

You can record an excellent capture of one room and an excellent capture of the next and still have almost nothing describing where they are relative to each other. Each reconstructs; together they do not.

The fix is a deliberate recording that travels between them — through the doorway, into the second space, and back again — keeping the camera oblique so that features from the first area, the doorway itself, and features from the second appear together in overlapping frames. That chain is what fuses two areas into one space.

Anywhere the space narrows or turns — doorways, corridors, arches, stairs, screens — deserves the same treatment.

## Occlusion

Rooms hide a great deal from any single route: behind chairs, between furniture, under tables, beside cabinets, around columns, inside alcoves, around door frames.

Come back to these deliberately. And do not simply point the camera into the gap from where you stand — move sideways, forward and back, or around the obstruction, while keeping the hidden area in view. Coverage plus translation, not coverage alone.

## Several recordings, not one long take

For anything complicated, several purposeful recordings beat one continuous take, provided they overlap strongly. You are not making independent scans; you are making deliberate pieces of one reconstruction.

The practical argument is that a ten-minute recording only supports one question — *have I filmed everything?* — which is not a useful question. Separate passes support better ones: have I established the geometry, is the ceiling connected to the upper walls, have I captured this wall from enough positions, are these two areas linked?

And if one pass is ruined by blur, exposure, or somebody walking through the shot, you repeat that pass rather than the session.

More footage is not better footage. Five overlapping, purposeful clips beat twenty disconnected ones.

## What to record well, and what to record thoroughly

Not every surface deserves equal effort. For spatial storytelling it helps to separate two things:

**Reconstruction-important.** What the space needs to stand up: walls, floor, ceiling, corners, doors, major furniture. This needs to be solid but not beautiful.

**Story-important.** What people will move closer to look at: photographs, personal objects, documents, artwork, signage, a particular chair. This needs genuine visual fidelity, because it will be inspected.

Capture the room well enough to be stable, then spend the remaining time on the things the story actually rests on. Deciding which is which before you start recording is most of the value — and it is the same judgement that shapes [04 — Story Collection and Interviews](04-story-collection-and-interviews.md). In practice the two are decided together, usually on the same visit.

<!-- FIELD NOTE: how the reconstruction-important / story-important split has played out on real sites — how the decision gets made, who makes it, and what has been regretted afterwards. -->

## Framing and lens

**Landscape is the sensible default** for interiors. It holds more horizontal context, so a single frame can contain foreground furniture, a corner, a wall and a doorway — which is what keeps the parts of the room connected.

Portrait is worth it for strongly vertical spaces: stairwells, narrow corridors, tall halls, floor-to-ceiling features. But do not choose portrait merely to reach floors and ceilings. Separate upward and downward passes do that better.

**Do not rotate the phone mid-recording.** Keep the orientation constant through a pass. If you need vertical coverage, change the camera angle, not the orientation.

**Use the main (1×) lens.** Ultra-wide is tempting indoors because it fits more of the room in, but it costs distortion, fine detail and low-light performance — and trackable detail matters more than field of view. Reach for 0.5× only in genuinely confined spaces.

## Doing this in Scaniverse

[Scaniverse](https://scaniverse.com/) handles a single room comfortably, processes on the device in about a minute, and costs nothing. Use **Splat** mode, and capture as described above — the app does not relieve you of designing the path.

Its limits show up on scale and on transitions. A large or complex interior, or a sequence of connected spaces, is usually better recorded as video and trained on a desktop, where you can give each pass its own recording and control how they combine.

<!-- FIELD NOTE: where Scaniverse has stopped being enough on real interiors — room size, session length, and what the failure looked like. -->

## Shooting video for desktop training

The settings are the same as for objects: highest resolution, lowest frame rate, exposure and focus and white balance locked before you start, short exposure and small aperture, high ISO accepted in preference to blur, no flash.

Indoors, two of these matter more than they do outside. Light is usually poorer, so the camera lengthens its exposure and any speed turns into blur — move slower than you think you need to. And rooms very often contain a bright window and a dark interior at once, which is the hardest exposure case there is; lock for the interior and accept the blown window rather than letting the exposure hunt between frames.

Record each pass as its own file, named for what it is. It makes the coverage check below possible, and it makes a re-shoot cheap.

## Before you leave

- Has every important area been seen from several positions, not just seen?
- Is the ceiling connected to the upper walls? The floor to the lower walls?
- Does every close-up have a chain of intermediate views back to the wider room?
- Are separate areas joined by footage that actually travels between them?
- Is anything important visible in only one pass?
- Did you rely on standing still and panning anywhere?

## In short

For an object, orbit it. For a room, weave through it.

The goal is not one perfect camera path. It is a connected web of positions and overlapping views — down from the whole room through zones, surfaces and objects to the details, and back up again — so that the reconstruction understands both the space and the things inside it.
