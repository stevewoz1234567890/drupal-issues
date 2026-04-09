# Note: Multi-tenant **RAG** with **Search API** + **ai** stack; **RagTool** dynamic filters ([#3584010](https://www.drupal.org/project/ai/issues/3584010))

**Projects:** [AI](https://www.drupal.org/project/ai) (`ai`), **ai_chatbot**, **ai_search**, [Search API](https://www.drupal.org/project/search_api) (`search_api`) — **community patterns** (Slack). **Provider** example in thread: **Amazee.ai**.

## Summary

Teams building **dashboard**-style sites where **each end-user tenant** must only query **their own** vector data in a chatbot stack often combine:

1. **Indexed metadata** — a **filterable attribute** (e.g. **`client_id`**) stored on **every chunk** / indexed document so the vector index can be filtered per tenant.
2. **Hard enforcement in PHP** — a **`SearchApiEvents::QUERY_PRE_EXECUTE`** (or equivalent) **event subscriber** that **always** adds conditions so the query only returns vectors allowed for the **current user’s** **`client_id`** (or set of allowed IDs). This is the **authorization boundary**—not optional LLM behavior.

Another implementer (**artem**) reported the **same** approach using **Azure Vector Database**, with **multiple** such filters where permissions are **more granular even inside a tenant**.

## Dynamic filters and the LLM

**m4olivei** described a follow-up: data also segmented by dimensions such as **year** and **type**, with a goal to let the **agent** supply those as **filters** in the **RAG** tool call (so retrieval narrows before or alongside embedding search).

**artem** noted that passing **filters from the LLM into the RAG tool** is interesting but to **treat tenant / identity filters as sensitive**: **restrict** what the model is allowed to set so a **prompt injection** cannot retarget retrieval to **another tenant’s** data.

## Upstream issue

**m4olivei** opened [**#3584010 — RagTool should support dynamic metadata filtering via additional context definitions**](https://www.drupal.org/project/ai/issues/3584010): the existing **RagTool** **FunctionCall** shape is **too rigid** for **additional** `context_definitions` (e.g. via alter hooks) so that **dynamic** metadata filters can be advertised to the LLM and applied to the **VDB** query—**`RagTool::execute()`** was reported to **ignore** those definitions.

Track that issue for productized support for **LLM-supplied** filters; keep **tenant isolation** enforced **server-side** regardless.

## References

- Issue: [drupal.org/project/ai/issues/3584010](https://www.drupal.org/project/ai/issues/3584010).
- Slack (paraphrase): **m4olivei** — **ai** / **ai_chatbot** / **ai_search** / **search_api**, **Amazee.ai**, **`client_id`** filterable attribute + **`QUERY_PRE_EXECUTE`** enforcement; **artem** — same pattern, **Azure** VDB, **multiple** filters; discussion of **LLM-driven** filters vs **prompt** safety; **#3584010** filed for **RagTool** flexibility.
