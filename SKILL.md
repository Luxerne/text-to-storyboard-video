---
name: text-to-storyboard-video
description: Turn prose, scripts, narration, concepts, or scene descriptions into a coherent shot list, generate matching first-frame and end-frame images for every shot, and write an image-to-video prompt that connects each pair. Use when the user asks for 分镜、首尾帧、关键帧、图生视频提示词, or a text-to-video preproduction package. Do not use for a single unrelated image or for video editing without source text.
---

# Text to Storyboard Video

Convert the user's text into a production-ready storyboard package. Complete the full workflow: plan shots, generate each shot's first and end frames, then write the prompt that animates between those exact images.

## Defaults

Honor every user-specified creative or technical choice. When details are absent, infer them from the text instead of blocking progress:

- Preserve the source language for titles and explanations.
- Default to cinematic realism unless the source strongly implies another style.
- Default to 16:9, 24 fps, and 4–6 seconds per shot.
- Use one shot per meaningful visual beat; merge repetitive beats and split actions that cannot be shown clearly in one continuous take.
- Avoid visible text in generated images unless the source explicitly requires it.

State important inferred defaults briefly before the storyboard. Ask a question only when a missing choice would substantially change the story or make image generation unsafe or impossible.

## Workflow

### 1. Analyze the source

Extract the narrative arc, subjects, locations, time of day, emotional progression, key actions, and any required dialogue or voice-over. Do not invent plot events that change the meaning.

Create a compact continuity bible before generating images:

- fixed character traits, clothing, age range, and distinguishing features;
- recurring props and their position or condition;
- location geometry, lighting direction, palette, weather, and period;
- global rendering style, lens language, aspect ratio, and color treatment.

For ambiguous visual details, choose one coherent interpretation and keep it fixed.

### 2. Design the storyboard

Read [references/output-format.md](references/output-format.md) and use its shot schema. Each shot must have a clear dramatic purpose and a physically achievable change between the first and end frames.

Prefer visual storytelling over explanatory prose. Vary shot size and camera placement only when motivated. Maintain screen direction, eyelines, lighting, wardrobe, identity, and prop continuity across adjacent shots.

### 3. Prepare frame prompts

For every shot, write two self-contained image prompts:

1. **First frame:** the exact state at the instant the shot begins.
2. **End frame:** the exact state at the instant the shot ends.

Each prompt must repeat the relevant continuity-bible details, composition, lens or shot size, lighting, palette, and aspect ratio. Describe observable visual facts rather than plot explanations.

The end frame must preserve identity, clothing, location, light direction, and art style. Change only what the planned action and camera movement require. Do not introduce new people, props, weather, or architecture unless the storyboard explicitly calls for them.

### 4. Generate the images

Use the available image-generation capability; do not stop at writing image prompts when generation is available.

- Generate the first frame before the corresponding end frame.
- Use the first frame as a visual reference for the end frame whenever the image tool supports references.
- Use established character or scene frames as references for later shots when that improves continuity.
- If an adjacent shot starts at exactly the previous shot's ending state, reuse that end image as the next first frame rather than generating a near-duplicate.
- Keep a stable filename or label scheme: `shot-01-first`, `shot-01-end`, and so on.
- Inspect generated results when inspection is available. Retry only frames with a concrete continuity, composition, or artifact problem, with at most two targeted retries per failed frame.

If image generation is unavailable, provide the complete storyboard and frame prompts, clearly identify that images remain ungenerated, and do not claim the package is complete.

### 5. Write the image-to-video prompts

Write each video prompt only after both frame images exist. Ground it in the visible content of the actual generated images, not just the original plan.

Each prompt must describe:

- the starting pose, composition, and spatial arrangement;
- subject motion and interaction in chronological order;
- camera movement and lens behavior;
- secondary motion such as hair, fabric, foliage, smoke, reflections, or light;
- pacing and intended duration;
- the precise final pose and composition matching the end frame;
- continuity constraints and unwanted changes to avoid.

Describe one continuous shot. Do not request cuts, scene changes, impossible teleportation, or off-screen events that cannot connect the supplied frames. Prefer concrete motion verbs and temporal phrasing such as “initially,” “then,” and “finally.” Keep stylistic adjectives subordinate to motion instructions.

### 6. Deliver the package

Return, in this order:

1. assumptions and continuity bible;
2. storyboard overview;
3. each shot's generated first and end frames, with labels or file links;
4. the final image-to-video prompt directly below its frame pair;
5. a compact prompt-only block suitable for copying into a video generator.

Keep shot numbering consistent across the table, images, filenames, and prompts. Explicitly note any frame that could not be generated or any continuity issue that remains.

