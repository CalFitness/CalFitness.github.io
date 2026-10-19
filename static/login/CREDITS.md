# Sign-in story photos

The five slides of the web sign-in story (`apps/web/src/auth/AuthStory.tsx`, copy in `shared/loginStory.ts`) — the same files as `apps/calfitness/assets/images/login/`. All from Unsplash,
under the [Unsplash License](https://unsplash.com/license): free for commercial use, no
attribution required — credited here anyway. Unsplash does **not** guarantee model or
property releases, which is why every slide is hands, objects or distant figures; keep it
that way when swapping one.

| File | Photo | Photographer |
|---|---|---|
| `lacing.webp` | [Lacing up at dawn](https://unsplash.com/photos/person-wearing-gray-and-white-nike-athletic-shoes-LiL_bYF8SeE) | Karmishth Tandel |
| `dosa.webp` | [Dosa, chutney and sambar on a leaf](https://unsplash.com/photos/dosa-with-chutney-and-sambar-breakfast-VIqcVqZ1uxM) | Zoshua Colah |
| `kettlebells.webp` | [Hands on two kettlebells](https://unsplash.com/photos/a-pair-of-hands-holding-two-blue-kettles-c-iX42QHg3w) | Mads Eneqvist |
| `path.webp` | [Two people on a lamp-lit path](https://unsplash.com/photos/a-couple-of-people-walking-down-a-dirt-road-1fiNXZ1W6Mg) | Dewang Gupta |
| `peaks.webp` | [Snow peaks at sunrise](https://unsplash.com/photos/snow-covered-mountain-peaks-bathed-in-golden-sunlight-PTA6j09gWEs) | Mayur Arvind |

## How they were made

Each is a 1170×2532 crop from imgix (`fit=crop&crop=focalpoint`, subject in the top 55%
so the copy and buttons own the bottom), with the charcoal-gold grade baked in — CSS
`saturate(0.78) contrast(1.06) brightness(0.92) sepia(0.14)` plus a soft-light gold wash,
the same grade `wireframe/login-story-photos.html` previews — rendered in headless Chrome
and encoded with `cwebp -q 60–72`. The five come to ~850 KB. Bake a replacement the same
way, or it will look like a different photographer.
