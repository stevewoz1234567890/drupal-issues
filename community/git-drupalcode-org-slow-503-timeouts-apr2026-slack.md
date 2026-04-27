# git.drupalcode.org — incidents (Apr 2026): **503** / **timeouts**, **CORS** + **GraphQL** from **www.drupal.org**

## A. Slow / 503 / clone flakiness

**Context:** Contributors asked whether [git.drupalcode.org](https://git.drupalcode.org/) was slow. Some saw **503** or **request timeout**; **DA** staff pointed to **active alerts** and **investigation** ([**#drupal-infrastructure** message](https://drupal.slack.com/archives/C51GNJG91/p1776416455244459) re **alerts**). `git clone` over HTTPS **failed** on **slower** links and **worked** on **faster** ones for some.

| Observation | Who / source |
|-------------|----------------|
| **503** / **Request timeout** | **Sivaji Ganesh** |
| Infra **alerts** on **git.drupalcode.org**; **investigating** | **fjgarlin** → [**#drupal-infrastructure**](https://drupal.slack.com/archives/C51GNJG91/p1776416455244459) |
| **`git clone`** … **drupal** flaky on **slow** **link**, OK on **fast** | **Chris Kelly** → [**#gitlab**](https://drupal.slack.com/archives/CGKLP028K/p1775935512355739) (**11 Apr 2026**) |

- **Retries**, shallow clones (`--depth=1`) during transient slowness. **Planned** maintenance **503** — [`../issues/09-git-drupalcode-org-gitlab-update-503.md`](../issues/09-git-drupalcode-org-gitlab-update-503.md). **Status** comms — [`../issues/18-drupal-org-public-status-page-infrastructure-3372242.md`](../issues/18-drupal-org-public-status-page-infrastructure-3372242.md). **Reporting:** UTC, URL/command, error text, network context.

---

## B. CORS: `www.drupal.org` → `git.drupalcode.org/api/graphql`

During the same **git.d.o** alert period, **penyaskito** saw the **GitLab ↔ drupal.org** issues **JS** integration break: fetches to `https://git.drupalcode.org/api/graphql` from `https://www.drupal.org` failed **CORS**—first the **preflight** (no `Access-Control-Allow-Origin`), then after **drumm** tweaked **edge** rules the **preflight** improved but the **main** request still had no **`Access-Control-Allow-Origin`**. **drumm** said it was **probably related** to the same incident and **adjusted rules** several times; he suggested opening **git.d.o** directly to complete any **“checking your browser”** / cookie path (**penyaskito** still errored while logged in; a colleague and **tedbow** reproduced). **tedbow** and **penyaskito** later saw recovery after **time** (dog-walk banter in thread). **drumm** made one more rule change before leaving and believed the **root cause** was then addressed (paraphrased: *figured out the correct way to solve it*).

| Who | Note |
|-----|------|
| **fjgarlin** | Services returning toward normal; still monitoring. |
| **longwave** | Joked about a **huge** **MR** **breaking** things; **#hugops**. |

### B2. Apr 20 follow-up — **mglaman** (interstitial / cookies)

Same **CORS** surface: `No 'Access-Control-Allow-Origin'` on `https://git.drupalcode.org/api/graphql` when called from `https://www.drupal.org`.

| Who | Note |
|-----|------|
| **drumm** | Visiting **git.d.o** directly should run the **“checking your browser”** interstitial and **allow** later cross-origin requests. |
| **mglaman** | Still broken after interstitial advice (**“**negative**”**); suspected **`fsch_…`** cookie could not be set (screenshot **2026-04-20**). |
| **drumm** | Reproduced; noted **GraphQL** ignores much of what works well for plain **HTTP**; shipped a fix. **“**This should be resolved now**”** (~2:02 PM thread time). |
| **mglaman** | Confirmed fixed (~2:12 PM). |

**Use:** Cross-origin **GraphQL** from d.o to **git.d.o** depends on **edge** **CORS** (and any **bot** / **challenge** layer). **Interstitial** + **cookie** paths can still **fail** **for** **some** **profiles** **(mglaman** **)**. When WAF or Fastly-style **rules** change, **OPTIONS** and the follow-up request can fail **independently**—compare both in the Network panel. Thematically related: [`../issues/07-api-drupal-org-fastly-interstitial-firefox.md`](../issues/07-api-drupal-org-fastly-interstitial-firefox.md) ( **api.drupal.org** , different host).

**See also:** **d.o** project page **repo** logos (`/-/avatar`) — [`drupalorg-project-page-logo-git-avatar-apr2026-slack.md`](drupalorg-project-page-logo-git-avatar-apr2026-slack.md).
