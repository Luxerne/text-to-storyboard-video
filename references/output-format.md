# Storyboard Output Format

Use the following fields for every shot. A Markdown table is suitable for the overview; use a dedicated section per shot for images and full prompts.

| Field | Required content |
|---|---|
| Shot | Stable ID such as `S01` |
| Purpose | Story or emotional function |
| Duration | Usually 4–6 seconds unless the action requires otherwise |
| Shot design | Shot size, angle, lens feel, composition, and camera movement |
| Action | Visible action in chronological order |
| First frame | Exact beginning state |
| End frame | Exact ending state |
| Audio | Dialogue, voice-over, ambience, or sound cue when relevant |
| Transition | Cut or motivated transition into the next shot |

For each detailed shot section, use this order:

```markdown
## S01 — Short title

**First-frame image:** [generated image or file link]

**First-frame prompt:** ...

**End-frame image:** [generated image or file link]

**End-frame prompt:** ...

**Image-to-video prompt:**
Beginning from [visible start state], [subject action in sequence]. The camera [camera motion]. [Secondary motion]. Over [duration], the movement [pacing], finally arriving at [visible end state that matches the end frame]. Preserve [identity, wardrobe, setting, lighting, style, and geometry]. Avoid [shot-specific failure modes].
```

The prompt-only block should retain shot IDs and durations but omit commentary:

```text
S01 | 5s | [complete image-to-video prompt]
S02 | 4s | [complete image-to-video prompt]
```

## Quality Checks

Before delivery, verify:

- every planned shot has a first frame, end frame, and connecting video prompt;
- the first and end images share subject identity, wardrobe, scene geometry, lighting direction, and style;
- each motion can plausibly occur within the stated duration;
- the prompt ends at the supplied end frame rather than merely resembling it;
- adjacent shots preserve screen direction and relevant props;
- filenames, shot IDs, and prompt IDs agree.

