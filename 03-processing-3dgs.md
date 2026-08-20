# Processing a Scan into a Usable 3DGS

Scanning produces footage. Processing turns that footage into a splat you can open, clean, and hand to something else. This guide covers the three routes that get you there, the one cleanup step they all share, and the hardware that actually limits which route is open to you.

## What this stage is doing

Every route performs the same two operations, whether or not it shows them to you.

**First, it works out where the camera was.** Each frame is matched against its neighbours, and from those matches the software solves for a position and orientation per frame, plus a sparse cloud of 3D points. This is Structure-from-Motion, and it is the step that fails when a capture was shot badly — insufficient overlap, motion blur, standing still and panning. Nothing downstream recovers from a bad solve.

**Second, it trains.** Starting from those points, the software fits a few million small translucent ellipsoids — the splats — adjusting position, size, orientation, colour and opacity over tens of thousands of iterations until the rendered scene matches the input frames. This runs on the GPU and takes minutes to hours.

A phone app does both on the device and shows you neither. The desktop routes separate them, which is the entire reason to use one: you can inspect the alignment before committing an hour to training, and you can retrain with different settings without re-solving.

![The three processing routes](diagrams/diagram-10-processing-routes.svg)

*The phone route performs both operations invisibly. The desktop routes expose them, which is what makes it possible to fix a bad solve without re-shooting, or retrain without re-solving.*

## Resolution: the setting that matters most

Before any route, one decision governs both how long processing takes and how sharp the result is, and the intuitive answer is wrong.

**More pixels do not buy more clarity.** The reference 3DGS implementation downscales any image wider than 1600px automatically, and its authors recommend leaving that behaviour in place. Above that width the extra pixels are discarded before training sees them. Worse, forcing full resolution often makes the result *softer*, not sharper: densification decides whether to split a splat by comparing a positional gradient against a fixed threshold, and the gradient a given piece of geometry produces depends on the render resolution. Thresholds tuned around 1600px under-densify above it, so you end up with fewer, larger splats covering more detail.

**Resolution is also the main lever on alignment time.** Feature extraction and matching scale with pixel count — COLMAP itself downscales above 3200px by default. Halving your working resolution is the cheapest speed-up available.

So: **capture high, process low.** Shoot 4K, then downscale to around 1600px wide before alignment. Downscaling a compressed 4K frame is not the same as shooting at 1080p — it retains more genuine detail, and it averages away sensor noise and codec artefacts that would otherwise mislead feature matching.

The exception is a subject with fine texture you intend to read at close range. Postshot's higher-quality profiles are documented as making use of higher-resolution detail, so there is some headroom there. Treat it as a deliberate choice for a specific scan, not a default.

## The three routes

| | Phone | Desktop, paid | Desktop, open source |
|---|---|---|---|
| Tool | Scaniverse | Postshot | Reflct → RealityScan → LichtFeld Studio |
| Cost | Free | Free to train, paid to export | Free |
| Hardware | A recent phone | Windows + NVIDIA GPU | Windows or Linux + NVIDIA GPU |
| Time to a splat | About a minute | 20 minutes upwards | An hour upwards |
| Control | None | Training settings | Every step |

The routes are not ranked. A small object captured well on a phone will beat a large site captured badly and trained for three hours.

## Route 1 — Phone, free

[Scaniverse](https://scaniverse.com/) does the whole pipeline on the device.

1. Install Scaniverse on your phone.
2. Open it and choose **Splat** capture.
3. Follow the on-screen guidance. The splat builds visibly as you move, which is useful — thin or missing regions show up while you can still walk back to them.
4. Stop capturing and let it process.
5. The finished scan appears in your gallery. Share the PLY from there to your laptop.

It costs nothing, needs no account, and processes in about a minute without sending your footage anywhere. For a single object or a single room it is often the right answer outright, and the file it gives you is a normal PLY that the rest of this guide applies to.

Its limit is scale and control. There are no training settings, so a scan that comes out soft comes out soft. Large or connected spaces, and anything where you want several passes combined deliberately, belong on a desktop route.

<!-- FIELD NOTE: how long a Scaniverse capture actually takes on site including retries, what it does to the phone's battery and temperature, and the point at which a scene has been too big for it. -->

## Route 2 — Desktop, paid

[Postshot](https://www.jawset.com/) takes video directly and handles alignment and training in one application. It is the shortest desktop path.

1. Import your video.
2. Either train immediately on the defaults, or set the parameters first. The three that matter:
   - **Max splat count** — the ceiling on how many splats the scene may use. Higher means more fine detail, a larger file, and more VRAM.
   - **SH degree** — how much view-dependent colour each splat carries. Higher degrees reproduce sheen, reflection and the way a surface shifts colour as you move around it, at the cost of file size. Lower degrees flatten the scene towards uniform colour but are much lighter.
   - **Training steps** — how many optimisation iterations to run. More steps sharpen the result with diminishing returns, and directly set how long you wait.
   - **Downsample images** — the working resolution, as above. Leave the downsampling on unless you have a specific reason to want the extra detail and a profile that can use it.
3. Wait. Twenty minutes is a short train; a large scene at a high splat count is considerably longer.
4. Export **PLY** for a lossless working file, or **SOG** for a compressed one.

**The free tier cannot export a splat.** It is non-commercial, it watermarks rendered output, and radiance field export is withheld. PLY and SPZ export, along with commercial use and watermark-free rendering, require the paid **Indie** tier. A further **Studio** tier adds HDR and RAW input, output above 4K, and a command line interface. Postshot is Windows-only.

If you intend to take the splat anywhere else — and this guide assumes you do — the free tier will not get you there. Pay for Indie, or use route 3.

## Route 3 — Desktop, open source

More steps, no licence, and you see every stage. This is the route to use when a scan matters enough to be worth re-running with different settings.

**1. Convert the video if you need to.** [HandBrake](https://handbrake.fr/) turns MOV into MP4. Skip this if your footage is already MP4.

**2. Extract sharp frames.** [Sharp Frames](https://sharp-frames.reflct.app/) by Reflct pulls full-resolution frames out of the video, measures each one for blur, and selects across the sequence rather than at a fixed interval. It runs entirely in the browser — the footage never leaves your machine — and accepts MP4, MOV and WebM. Use Chrome, and note the roughly 1.9 GB file ceiling that browser memory imposes; long captures need splitting.

Aim for frames that overlap by about 80%. Reflct's own guidance is to sample at ten or more frames per second and keep the sharpest of every five, which lands near one frame every half second. A modest dataset is around 100 images; a large one runs to 1000 or more. Past that you are mostly adding near-duplicate views, which costs training time and can degrade the result rather than improve it.

**Downscale the extracted frames to around 1600px wide before the next step**, for the reasons above. This is where the resolution decision actually gets made, and it is the difference between an alignment that takes minutes and one that takes hours.

**3. Screen the frames yourself.** Open the folder and delete anything the blur measure let through: frames with people walking through them, frames where the exposure hunted, frames of a wall and nothing else. This takes ten minutes and is the highest-value ten minutes in the route.

**4. Align.** [RealityScan](https://www.realityscan.com/) — formerly RealityCapture — solves camera positions from the frames. It is free for students, educators, and individuals or companies under $1 million USD in annual gross revenue; a paid licence is required above that.

Import the images, align them, and look at the camera path before going further. A good alignment produces **one clean, continuous camera track**. If it has broken into several separate tracks, some of your frames did not overlap enough for the solver to join them. Remove those frames and align again, or delete the stray track so that only the intact one is exported.

**5. Export the registration in COLMAP format.** This writes out the camera poses and sparse points in the layout every trainer understands.

On distorted versus undistorted images: export the **original distorted** images and enable 3DGUT in training, which is the better path now that RealityScan 2.1.1 has fixed the quality loss its COLMAP export used to introduce on distorted images. Export undistorted images only if you are training with something that assumes a plain pinhole camera. Undistorting throws away pixels at the frame edges, so avoid it when you do not need it.

**6. Train.** [LichtFeld Studio](https://lichtfeld.io/) loads a COLMAP dataset and trains, inspects and exports from one application. It is GPL-3.0: build it from source for nothing, or make a contribution to get the prebuilt Windows binary. Windows and Linux, NVIDIA only.

**7. Set the parameters.** Max splat count and training steps behave as they do in Postshot. Two more are worth knowing:
   - **3DGUT** — replaces the standard projection with one that handles distorted camera models directly, so fisheye distortion and rolling shutter are modelled rather than corrected away. This is what lets you feed it the distorted images from step 5.
   - **PPISP** — compensates for photometric variation between frames, the auto-exposure and auto-white-balance drift that a phone introduces across a pass. Worth enabling when your frames were not shot with locked exposure, which is to say most of the time.

**8. Train and inspect.** The result appears in the application's own viewer, so you can judge it before exporting.

**9. Export** PLY, SOG or SPZ.

## Cleanup — SuperSplat

Every route produces a file that needs tidying. Almost every scan carries floaters: stray splats hanging in the air where the solver had too little information, usually over featureless surfaces, near reflections, and around the edges of the captured volume.

[SuperSplat](https://superspl.at/editor) from PlayCanvas is free, MIT-licensed, and runs entirely in the browser with nothing to install. Load the PLY, select the debris and delete it, crop the scene to what you actually want, and export.

Do this before compressing, not after. Compression is lossy, and there is no reason to spend bits on splats you are about to remove.

## Formats

**PLY** is the working format. It is uncompressed and lossless, it is what every tool here reads and writes, and it is large.

**SOG** is for delivery. PlayCanvas's compressed format is 15–20× smaller than the equivalent PLY, at the cost of being lossy. This is what you publish.

**SPZ** is Niantic's compressed format, around 10× smaller, also lossy, and MIT-licensed. Scaniverse writes it natively.

The rule is simple: **train and edit in PLY, convert to SOG once, at the end.** Never edit a compressed file and re-compress it.

## What the machine needs

Training is CUDA work, so the hard requirement is an **NVIDIA GPU**. AMD and Intel graphics will not run any of the desktop trainers here, and neither will Apple Silicon.

- **Compute capability 7.5 or newer** — an RTX 2060 or better, or a GTX 16-series card. GTX 10-series and older are out.
- **8 GB VRAM minimum.** This is a floor, not a target; large scenes at high splat counts will exceed it.
- **32 GB system RAM** for comfort on anything substantial.
- **Windows** for Postshot. Windows or Linux for LichtFeld Studio.
- A recent NVIDIA driver — LichtFeld Studio needs 570 or newer for CUDA 12.8.

If you do not have that machine, the phone route needs none of it, and SuperSplat runs on anything with a browser. Between them you can capture, clean and publish without ever owning a training GPU — you simply give up control over training.

<!-- FIELD NOTE: actual training times and VRAM use on the machine you use, per route, for a typical object and a typical room. -->

## Choosing between them

Start on the phone. It is free, it is fast, and it tells you within a minute whether the capture was any good — which is worth more than a better trainer applied to worse footage.

Move to Postshot when you want control and would rather pay for a licence than assemble a pipeline.

Use route 3 when the scan matters: when you need to see the alignment before training, retrain without re-solving, keep everything local, or work without a licence.

## Taking the splat into the engine

Engine-specific import and orientation details are documented in the Spatial Storytelling Engine repository, in [`docs/GAUSSIAN-SPLATS.md`](https://github.com/IntoStorymode/Spatial-Storytelling-Engine/blob/main/docs/GAUSSIAN-SPLATS.md).

## In short

- Two operations, always: solve where the camera was, then train the splats.
- Capture high, process low. Shoot 4K, downscale to about 1600px wide before alignment.
- Three routes: phone for speed, Postshot for control behind a paid export, open source for control at no cost and more steps.
- Postshot's free tier cannot export a splat.
- Clean in SuperSplat before you compress.
- Work in PLY. Deliver in SOG.
- Training needs an NVIDIA card, compute capability 7.5 or newer, 8 GB VRAM.
