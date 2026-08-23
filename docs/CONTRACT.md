# Motion contract

Do not implement against folklore. Implement against this file.

## Identity

- Product: **Motion**
- Repo: `computerpets-motion`
- Category: AI & GPU
- Idea: Procedural Animator
- Port / surface: `8093`

## Must

- Stay canon with 210 species. No illegal hybrids. No swapped voices.
- Treat the desktop overlay as the main quest. This organ is optional until wired.
- Fail soft: the overlay keeps walking if this service is down, unless this *is* the overlay.
- No PII in public artifacts (Steam id, wallet, home path, webcam frames).

## Data

Rig(speciesId, bones[]) · Clip(verb, fps, frames, loop) · BakeJob(id, status)

## Surface

- POST /v1/clip — {speciesId, verb, seed} → sprite sheet + json timings
- GET /v1/rig/{speciesId} — bone lengths, IK limits
- POST /v1/bake — overnight batch bake of the 210 default cycles

## Neighbors

- computerpets desktop renderer
- computerpets-atelier (new trait meshes)
- computerpets-gaze (gesture-driven clips)

## Failure doctrine

CUDA absent → CPU bake, warn once. Impossible IK → snap to rest pose. Bake fail → keep last good clip, never a T-pose on the desktop.

## Stack

Python 3.12 · PyTorch · CUDA skeletal solver · sprite sheet exporter · gRPC clip server
