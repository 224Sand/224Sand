### Sandeep Chavan

**I build systems that know when to say no.**

Ten years delivering enterprise software — a CPQ platform for 1,500 sales engineers,
$1–3M logistics programs — and I build the AI systems myself rather than only the
roadmap for them. The work below shares one idea: a system that cannot decline is a
system whose confidence means nothing.

---

#### [SandScope](https://github.com/224Sand/sandscope) · [live](https://sandscope-web.vercel.app)

An agent that answers incident and change-management questions over a fixed corpus —
and refuses when the retrieved evidence will not support an answer. Anything can
answer; the engineering is in knowing when not to.

The two refusal thresholds are not chosen by taste. They are read off the ROC curve
against explicit, asymmetric error budgets, measured over **715 labelled questions**:

| | measured | 95% CI | budget |
|---|---|---|---|
| False answers | 4.7% | [2.9, 7.6] | 5% |
| False refusals | 2.3% | [1.2, 4.3] | 10% |

An earlier build of that gate reported **0% false answers on 22 questions**. The real
rate on 534 was **56.6%**. Deriving the bands from error budgets rather than from a
good-looking sample is what fixed it, and the postmortem is in the repo — along with
three probe suites that are *expected to fail*, because a passing probe suite would
mean it had stopped looking.

Trained offline, served as ONNX with no training framework in the image. Runs on **$0
of infrastructure, enforced by a test.** Nine sprints under eleven named delivery
roles, where a requirement claiming `Done` while the test it names is absent fails the
build.

#### [charter](https://github.com/224Sand/charter) · MCP server

The governance from that build, extracted so anyone can run it. It makes a coding
agent work as named specialists and enforces the separation: **a role must produce a
machine-checkable artifact before it may sign off, and no role may sign off its own
work.** QA's contract is a test charter actually runs and rejects unless it genuinely
fails.

Pointed at its own codebase twice. The first run *did not finish* — it refused a
submission it could not verify, and that rejection exposed a dependency bug that would
have broken every install. [Both audits are published, rejections
included](https://github.com/224Sand/charter/tree/master/docs/self-audit).

---

#### Primitives

Small, dependency-light pieces from the same thesis.

| | |
|---|---|
| [resilient-llm-router](https://github.com/224Sand/resilient-llm-router) | Failover across providers — time-boxed disabling, cost-aware ordering, deterministic caching |
| [ground-truth-lock](https://github.com/224Sand/ground-truth-lock) | Path-locked fields and invented-number detection at the LLM-to-consumer boundary |
| [role-firewall](https://github.com/224Sand/role-firewall) | Deterministic input classifier — typed rules with reasons, first match wins, no LLM |
| [zero-llm-fallback](https://github.com/224Sand/zero-llm-fallback) | Useful output when every provider is down — pure-Python templates, no model |

---

**Working on:** agent reliability · evidence gating and refusal · LLM infrastructure ·
delivery governance that is enforced rather than documented

Hyderabad, India · open to Technical Program Manager / AI Program roles ·
[LinkedIn](https://linkedin.com/in/sandeep-c04)
