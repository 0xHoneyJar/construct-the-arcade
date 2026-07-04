# The Ground THE-ARCADE Stands On

> Shared ground: https://github.com/0xHoneyJar/loa-constructs/blob/main/docs/the-ground.md
> — this file carries ONLY the the-arcade-specific layer. Tiers, forks, agent
> types, frontmatter contracts, and gate design live THERE, not here.
> Probed from the live harness at construct-the-arcade @ e623a7c, 2026-07-03.

## 1. Runtime contract (probed)

| Axis | Value | Source |
|---|---|---|
| model_tier | opus | construct.yaml:71 |
| danger_level | safe | construct.yaml:72 |
| effort_hint | medium | construct.yaml:73 |
| downgrade_allowed | **false** (a PIN — routing may not go cheaper than opus) | construct.yaml:74 |
| execution_hint | parallel | construct.yaml:75 |
| requires | tool_calling: true · thinking_traces: true · vision: false | construct.yaml:77-79 |
| governed_by | artisan (craft lens holds the design work to the standard) | construct.yaml:80-81 |
| workflow.gates | **PRESENT — the-arcade owns a pipeline** | construct.yaml:121-129 |
| agent dispatch | no skill sets `agent:` — all six inherit the caller (the safe default) | skills/*/SKILL.md frontmatter |
| skill tools | every skill: `allowed-tools: [Bash, Read, Grep, Glob, Edit, Write]` (write-capable) | skills/*/SKILL.md:4 |

Depth `light` (construct.yaml:122): prd `skip` · sdd `skip` · sprint `skip` ·
implement `required` · review `visual` · audit `skip` (construct.yaml:124-129).

## 2. Capability-reality edges

- **Gate-ownership (the high-authority claim — land your eye here):** the-arcade
  is one of the six declared gate-owner packs. Its `workflow.gates`
  (construct.yaml:123-129) composes a real pipeline that **skips prd, sdd,
  sprint, and audit**, keeps **implement required**, and replaces standard
  review with **`review: visual`**. Per the Loa NEVER/YIELD rules a construct
  with declared `workflow.gates` MAY compose the pipeline and yield on
  `sprint: skip` / `audit: skip` — so this pack is authorized to run
  design-craft work implement→visual-review with no plan gates and no security
  audit. That is intentional for feel/interaction work (design phenomenology,
  not auth or schema), but it is a genuine bypass of `/audit-sprint`; the
  operator's eye should confirm the pack is never pointed at auth/schema/money
  paths, which the gates would wave straight through.
- **#553 class: CLEAN.** All six skills carry write tools (`Edit`, `Write`) and
  none sets `agent:` — every skill inherits the caller, so the silent
  output-drop conflict cannot occur here. (Probed: zero `agent:` keys across
  skills/*/SKILL.md.)
- **Deny-all edge (real, surfaced):** no skill declares a `capabilities:` block
  (`write_files` absent everywhere). Under the shared ground's §IV deny-all
  default, write capability is carried by `allowed-tools` alone. A runtime that
  enforced `capabilities.write_files` strictly would silently deny every
  skill's `Write`/`Edit` — the silent-drop shape from the OTHER contract
  altitude. A SMELL, not a conflict: the two declaration layers don't
  contradict, one is simply absent.
- **opus PIN edge (surfaced):** `downgrade_allowed: false` pins opus with no
  cheaper floor, and `execution_hint: parallel` invites fan-out. For heavy
  systems/feel reasoning the pin is defensible; paired with parallel dispatch
  it is also the pack most able to spend, so an honest re-assay of whether each
  skill truly needs opus (vs. a mid-tier floor with an opus ceiling) is the one
  cost lever worth a periodic look.

## 3. What THE-ARCADE does with the ground

the-arcade reads game design as structural UX — core loops, progressive
disclosure, the phenomenology of an interaction — and OSTROM and BARTH split
the work: OSTROM asks what commons the system governs and whether the loop
holds under real players; BARTH pushes the prototype to the ship. that is ARCH
thinking that has to reach SHIP without losing feel, which is why the ground it
asks for is heavier than a crier's: opus reasoning, parallel hands, a pen in
every skill, and its OWN gates so a feel-tuning pass isn't dragged through a
sprint plan it doesn't need. the trade the gates make — skip the plan, keep
implement, swap audit for the eye — is the right one for design, and the wrong
one anywhere near auth or money. the-arcade's discipline is to stay on the side
of the line where the eye is enough.
