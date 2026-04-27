# `hook_ENTITY_TYPE_view()` and hiding view output — `#access` depth, `unset()`, TAC Lite + Paragraphs (Slack)

**Context:** While adding **Paragraphs** support to [**TAC Lite**](https://www.drupal.org/project/tac_lite), **damienmckenna** needed to hide entity view output from `hook_ENTITY_TYPE_view()`. Setting `$build['#access'] = FALSE` on the top-level build did not suppress what appeared on the page.

## Suggestions (thread)

| Approach | Notes | Who |
|----------|--------|-----|
| `unset()` on parts of `$build` | First-pass option; same approach worked on an older version of the site | **Chi**; **damienmckenna** |
| `hook_entity_field_access()` | Field-scoped access | **Chi** |
| `#access` on the correct **depth** | Extra wrapper levels: top-level `#access` may not do what you expect—set on the **child(ren)** that actually render, e.g. `$build['field_foo']['#access']` | **FeyP** |
| `#access` on **each** field | Loop field render entries and set `#access` per field instead of only rewrapping the whole tree | **damienmckenna**, **LittleCoding** |
| Prefer `#access` over `unset()` when possible | Non-destructive; easier for later alter hooks | **LittleCoding** |

## Caching

- **LittleCoding:** Keep **cacheability** (contexts, tags, max-age) **aligned** with the **access** decision that drives visibility; even `#access` requires correct **cache** metadata so users do not see **stale** allowed/denied output.

## Use

- **Debug** unresponsive top-level `#access`: dump **`$build`** to see **nesting**; the **element** the **Renderer** **honors** may sit under **field formatters**, **Paragraphs**, or **layout** **wrappers**.
- **Prefer** `hook_entity_field_access()` for **field**-**level** **policy**; use **view** build hooks when you must reshape **composed** output.
- For **TAC** **Lite**-style **integrations**, **document** which **hooks** run per **bundle** / **view mode** so **cache** and **access** **logic** do not **diverge**.
