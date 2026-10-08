# video-skills

Agent skills for making videos with HTML, from [HeyGen HyperFrames](https://github.com/heygen-com/hyperframes).

Installed with:

```bash
npx skills add heygen-com/hyperframes --full-depth --yes
```

- `.agents/skills/` — the skills themselves
- `.claude/skills/` — symlinks so Claude Code picks them up
- `skills-lock.json` — installed versions
- `test-video/` — a 10-second animated-text test composition (Hebrew)

Render the test video:

```bash
npx hyperframes browser ensure   # once, downloads headless Chrome
cd test-video && npx hyperframes render
```

GSAP is vendored in `test-video/assets/` because the render browser can't always reach a CDN.
