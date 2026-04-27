# imagemagick — GIF→WebP, animation, event subscriber vs toolkit (Slack)

**Context:** **berdir** asked **mondrake** about [**#3295470**](https://www.drupal.org/node/3295470) (*Convert image effect / GIF to WEBP loses animation*) and an **MR** **reroll** that **moved** logic into an **event** **subscriber**. The old **hook** passed the **imagemagick** **toolkit**; that **path** was **deprecated** in **8.x-2.5** and **removed** in **8.x-3.0** (Jan 2020), so **`getFrames()`**-style access from the **subscriber** was **unclear** **without** **new** **APIs**.

## mondrake’s pointers

| Goal | How |
|------|-----|
| Frame count in the source file | File metadata: `$file_md->getMetadata(ImagemagickToolkit::FILE_METADATA_PLUGIN_ID, 'frames_count')` (as **mondrake** described). |
| Frames selected for this exec (CLI args) | `$event->getExecArguments()->getSourceFrames()` — see [**ImagemagickEventSubscriber.php** (5.0.x, ~L410–411)](https://git.drupalcode.org/project/imagemagick/-/blob/5.0.x/src/EventSubscriber/ImagemagickEventSubscriber.php?ref_type=heads#L410-411). |
| Architecture | **mondrake** prefers not passing a stateful **toolkit** through the event; long-term fit with **core** [**#3574822**](https://www.drupal.org/project/drupal/issues/3574822) (stateless `ImageToolkit` / `ImageToolkitOperation`). |

## berdir’s clarification

- `getExecArguments()->getSourceFrames()` reflects what is (or is not) set for this **ImageMagick** invocation, not always the file’s natural frame count; bundled subscriber code may only set it when unset (fallback).
- **berdir** used **`frames_count`** from **file** **metadata** alongside existing **coalesce**-style logic; that path addressed the case without depending on the **getSourceFrames** fallback.

## References

- **Original** **issue:** https://www.drupal.org/node/3295470  
- **Stateless** **toolkits** **(core**): https://www.drupal.org/project/drupal/issues/3574822  

## Use

- **imagemagick** 3.x+ and image effect authors: for multi-frame GIF→WebP (and similar), get **frame count** from **file** **metadata** first; use `ExecArguments::getSourceFrames()` to reason about the **current** **exec**-time frame selection, not always as a substitute for intrinsic file frame count.
- **Core** issue [**#3574822**](https://www.drupal.org/project/drupal/issues/3574822) explains why **mondrake** wants to avoid shoving a **stateful** **toolkit** into **events** long term.
