# Scanning Objects

This guide covers anything you can stand outside of and look inward at: a bowl on a table, a carved doorframe, a statue, a shopfront, a whole building. The scale changes enormously. The method barely changes at all.

Rooms and interiors are the opposite case — you are inside the thing you are recording — and are covered in [02 — Scanning Environments](02-scanning-environments.md).

## The principle everything else follows from

> Move the camera through space while repeatedly observing the same surfaces.

Reconstruction software works by finding the same visual feature in several frames and asking where the camera must have been for that feature to appear in those positions. It needs the feature to shift against its background between frames. That shift is parallax, and it only happens when the camera itself moves.

This is why standing in one spot and panning across a subject produces almost nothing usable. You have recorded a panorama. The camera's optical centre barely moved, so there is no displacement to measure and no depth to recover.

Rotation is not movement. Take a few steps.

<!-- DIAGRAM: rotation vs translation. Left: camera fixed at one point, view cone sweeping across subject, no parallax. Right: camera at three separate positions along a path, all pointing at the same subject, showing feature displacement. -->

## Before you start

Walk around the subject once without recording. You are looking for four things.

**Can you get all the way round it?** If yes, plan orbits. If not — a building on a street corner, a cabinet against a wall — plan to move along it and around whatever corners you can reach.

**Is it going to hold still?** The ideal subject does not change while you record. Leaves, flags, water, people, screens showing video, and doors that open all cause trouble.

**What is going to be difficult?** Mirrors, polished metal, glass and gloss reflect differently from every angle, so the software may read a reflection as solid geometry. Large blank surfaces have no features to track at all. Neither rules out a scan; both are worth knowing about before you start rather than after.

**Where is the light coming from?** Bright overcast is close to ideal — even illumination from every direction, no hard shadows. Direct sun is the hardest common condition, and low-angle sun is the worst of it.

## The establishing orbit

Start with one slow loop at chest or eye height, far enough back that the whole subject stays in frame.

This first pass is the frame everything else hangs on. It tells the reconstruction how the subject fits together, which lets later close-up passes find their place. Do it first, and do it completely — end where you began, so the loop closes.

Move slowly. Slower than feels natural; roughly the pace of someone reading a label in a museum. Speed costs you sharpness, and a blurred frame carries very little usable information.

### How much overlap

Adjacent views need to share a substantial amount of visual information — enough that the software can recognise one as a continuation of the other.

Two rules of thumb, either of which works:

- Around **60–70% overlap** between neighbouring views, for handheld video.
- No more than about **30° of viewpoint change** between one view and the next.

The second is easier to judge while walking. Thirty degrees around a subject is a small step, not a stride.

The floor beneath both: every surface you care about should be clearly visible in **at least three** frames taken from different positions. Once is not coverage.

Different tools state this differently, and the numbers are not interchangeable — Postshot, for instance, asks for only 30–50% overlap between images. Capture to the higher figure and you will satisfy the lower one.

## Change your height

One orbit at eye level leaves most subjects half-recorded. Everything facing up or down was seen only at a glancing angle, or not at all.

Repeat the loop at three heights:

- **Eye or chest level**, camera roughly horizontal. The sides, and the overall shape.
- **High, angled down.** Tops of things — shoulders and heads of statues, ledges, sills, upper mouldings, the tops of furniture and machinery.
- **Low, angled up.** Undersides, bases, overhangs, the underside of a table, the parts of a carving that only a shorter person ever sees.

A slow spiral from low to high as you circle works as well as three separate loops, and is quicker. What matters is that the subject gets observed from a range of vertical positions, not that the loops are tidy.

Do not worry about keeping the camera level. Tilting up and down is the point. Just make sure you are tilting *while moving* — tilt on its own, from a fixed spot, buys you nothing.

<!-- DIAGRAM: three orbit rings at low, eye and high level around a statue, camera angled up, level and down respectively. Show the vertical coverage each ring contributes. -->

## Change your distance

Once the shape is established, go round again closer.

Work down in steps: the whole subject, then a region of it, then the detail. Each step should still contain something the previous step also saw. Those shared features are what tell the reconstruction where the close-up belongs.

Jumping straight from the whole statue to a tight shot of one eye tends to fail. Nothing in the close frame connects it to anything else, so it floats. Approach in stages instead — whole, half, region, detail — and keep some surrounding context in frame even at the closest range. The edge of a plinth, a hand, a bit of the wall behind: enough to anchor it.

This is the one place where two common pieces of advice appear to disagree. Some guides tell you to hold a constant distance while orbiting; others tell you to vary your distance. Both are right about different things:

> Hold your distance steady **within** a pass. Change it **between** passes.

Drifting in and out mid-orbit makes a single pass inconsistent. Doing a second orbit deliberately closer gives you detail the first could not reach.

<!-- DIAGRAM: wide, medium and detail views as three nested frames on a statue, with shared features marked between each pair to show the connecting chain. -->

## Corners, and subjects you cannot circle

Plenty of subjects cannot be walked all the way round. A building on a street. A monument against a wall. A cabinet in an alcove.

The principle does not change; only the path does. Move along the subject rather than standing back and panning across it. Every step gives each part of the façade a slightly different angle, which is exactly what you need.

Corners deserve particular care, because they carry strong three-dimensional information and they are what joins one face of a subject to the next. Do not finish one façade, stop, walk round, and start again on the other. Curve continuously around the corner instead, keeping both faces in frame while they are both visible, and letting the second gradually take over.

Handled that way, a corner acts as a bridge. Handled badly, it is where a reconstruction splits into two unrelated halves.

<!-- DIAGRAM: camera path curving around a building corner, with frames at three points showing both façades visible simultaneously through the turn. -->

## Keep the passes connected

Overlap matters between passes just as much as between consecutive frames.

Your wide orbit, your closer orbit and your detail shots should each contain ground the previous one covered. If a doorway appears in the wide pass, again in the medium pass, and then in close-up, there is an unbroken visual path from that detail back to the whole building.

The failure to avoid is recording the front of something in one session, the back in another, and nothing that ties them together. Several short passes are fine — better than one long take, usually, since you can redo a bad one — but they have to overlap.

<!-- DIAGRAM: contrast a dense grid of camera positions with shared sightlines against four isolated positions with no overlap. Caption the difference as connected vs isolated observations. -->

## Conditions

**Move slowly and smoothly.** Avoid fast walking, sudden swings, whip pans, abrupt direction changes. Good capture footage is boring to watch, which is the correct outcome — you are collecting viewpoints, not filming.

**Watch for motion blur**, especially indoors and in low light, where the camera lengthens its exposure and punishes any speed. Good light helps tracking as much as it helps the picture.

**Keep the light stable.** Surfaces should look roughly the same from every angle. Even indoor lighting and bright overcast are the easy cases. Harsh sun, moving cloud shadow, spotlights, and the extreme contrast between a bright window and a dark interior are the hard ones.

**Watch your own shadow.** Outdoors in sun, your shadow travels across the subject as you orbit it, so the surface appears to change between frames. Keep it off the subject, or work in overcast.

**Texture helps.** Brick, stone, grain, wear, ornament and printed detail all give the software something to hold on to. If part of your subject is a blank painted panel, keep the textured surroundings in frame while you record it — the surroundings carry the tracking through.

## Doing this in Scaniverse

[Scaniverse](https://scaniverse.com/) is the shortest path from a phone to a usable splat, and the recommended starting point for most people. It is free, runs on iOS and Android, processes on the device in about a minute, and uploads nothing unless you ask it to.

Choose **Splat** rather than mesh or LiDAR mode. Then capture as described above — the app does not remove the need to orbit properly, change height, or move slowly. It removes the need to think about frame extraction, camera solving and training.

Export as **PLY** if the scan is going on to a desktop tool for cleanup, or **SPZ** if you want the compressed version straight away. Both are covered in [03 — Processing to 3DGS](03-processing-3dgs.md).

Its practical limit is scale. A single object, a monument, a room: comfortable. A whole building exterior in one capture: less so.

<!-- FIELD NOTE: Scaniverse in practice — how long a real object scan takes, capture-size limits actually hit, battery and thermal behaviour on a long session, and when it is worth abandoning the app for video. -->

## Shooting video for desktop training

For subjects Scaniverse cannot hold, or when you want more control over the result, record video and train it on a desktop.

- Record in the **highest resolution** available, and the **lowest frame rate**. Postshot typically samples only 2–3 frames per second from an imported video, so a high frame rate costs you storage and buys you nothing.
- **Lock exposure, focus and white balance** before you start. Auto settings drifting mid-capture is a common cause of failure — the same surface changing brightness between frames confuses the solver.
- Favour a **short exposure and a small aperture**. Reconstruction tolerates image noise considerably better than it tolerates blur, so raising ISO to keep the shutter fast is the right trade.
- Prefer the **main (1×) lens**. Ultra-wide fits more in, at the cost of distortion, detail and low-light performance.
- Do not use flash.

<!-- FIELD NOTE: kit actually used — phone vs camera, stabilisation, and whether the desktop route has proved worth the extra time for heritage subjects. -->

## Worked patterns

**A desktop object.** Establishing orbit at eye level. Second orbit high, angled down. Third orbit low, angled up. A closer partial orbit. Detail passes on what matters. A final pass over anything the first four missed.

**A statue or monument.** Full orbit at normal height with the whole thing in frame. Closer orbit on the main body. A pass on the upper parts from as high as you can get. A low pass for the base and undersides. Detail on the face, the inscription, the plaque — keeping some surrounding structure in frame throughout.

**A building.** Wide pass along or around it from a distance, capturing the whole structure. Closer pass for façades and major features. Repeat sections while tilting up and down. Deliberate movement around every corner you can reach. Detail on entrances, windows, signs, stonework. A final pass for anything seen from only one position.

## Before you leave

- Has every important surface been seen from at least three positions?
- Is there a chain of overlapping views from each close-up back to the whole subject?
- Did the establishing loop actually close?
- Are the passes connected to each other, or are they separate recordings of the same thing?
- Did you rely on standing still and panning anywhere?

The last one is worth checking honestly. It is the most common way a capture fails, and it always feels productive at the time.

## In short

> Circle it. Change height. Change distance. Keep overlapping.

And where you cannot circle it:

> Move along it. Go around the corners. Come back to it from different heights and distances. Keep every pass visually connected to the others.
