---
{"dg-publish":true,"permalink":"/wiki/technology/ai/open-claw/kimi-k3-agent-team/","dg-note-properties":{}}
---

Starter Prompt:
> Complete the entire project and don't stop until all success criteria are met and the product is ready for me.[^1]


In an average start-to-finish session here are how many tokens each of my agents consumed:

| Agent        | Sessions | Total Tokens | Avg Tokens/Session | % of Total |
|--------------|----------|--------------|--------------------|------------|
| orchestrator | 4        | 37,517,602   | 9,379,400          | 35%        |
| qa           | 58       | 22,873,097   | 394,364            | 21%        |
| backend-dev  | 72       | 19,711,261   | 273,768            | 18%        |
| frontend-dev | 59       | 9,684,485    | 164,144            | 9%         |
| adversary    | 13       | 4,413,441    | 339,495            | 4%         |
| general      | 15       | 3,945,957    | 263,064            | 4%         |
| infra        | 26       | 1,211,471    | 46,595             | 1%         |
| explore      | 2        | 511,436      | 255,718            | <1%        |
| build        | 13       | 442,593      | 34,046             | <1%        |
| platform-ops | 1        | 41,390       | 41,390             | <1%        |

# Adversary

 4% token spend for catching data-loss bugs, white-screens, and race conditions is a bargain compared to the cost of those hitting production.

**What's working well:**

- The adversary consistently finds **real, actionable bugs** — not theoretical edge cases
- Many findings are **HIGH severity** (data loss, crashes, concurrency bugs)
- All found bugs were **reproducible** with clear evidence (screenshots, API logs)
- The adversary found issues **QA missed** (bible white-screen, concurrency race conditions)
- 4% token budget for catching bugs that would hit production is a strong ROI

---

[^1]: Donner, Edward. "[I Let Kimi K3 Manage 4 AI Agents to Build an Entire App In 12 Hours](https://youtu.be/3pxv4WGs7KE?is=m8_eXyis1D7U9e8r)." *YouTube*, 2026.
[^2]: Donner, Edward. "[Personal Space](https://github.com/ed-donner/personal-space)." *GitHub*, 2026.
[^3]: Obra. "[Superpowers](https://github.com/obra/superpowers/blob/main/docs/README.opencode.md)." *GitHub*, 2026.
[^4]: Donner, Edrward. “[Harness Engineering Crash Course](https://youtu.be/t1PXvg2FceU?is=9M2RdnG0Ie_4Oi4R).” *YouTube*, 2026. 