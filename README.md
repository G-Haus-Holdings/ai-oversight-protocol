# Human Oversight Protocol for Multi-Agent AI Development

**Author:** Jeremiah Adonis Grey, founder of G Haus Holdings and Stratom Technologies; U.S. Army logistics captain
**Status:** In daily production use since 2026 across every Stratom Technologies product, including ThreadLane

---

## Why This Exists

I don't write code myself. I build software by directing AI agents. That makes one problem unavoidable: AI agents are highly capable, and they can also report work as finished, tested, or reviewed when it isn't, and they sound equally confident either way.

In the Army, I've been accountable for more than $500 million in property and have moved 500+ pieces of equipment at a time with zero loss or damage. That record doesn't come from trusting reports. It comes from systems that verify them: inventories, hand receipts, inspections, and a clear line on who can sign for what.

This protocol applies the same discipline to AI agents. It defines who does what, what counts as evidence, and which actions no agent may take without a human's explicit approval.

---

## Core Principles

1. **Agents execute and verify; the human decides.** My role is vision, priorities, and final approval. Agents do the engineering and must check their own work before it reaches me.
2. **Unverified work is not finished work.** Nothing is presented as done until it has been tested against the agreed specification and acceptance criteria.
3. **Approval is explicit, never inferred.** A plan I've approved authorizes work within that plan's scope only. Silence, a "your pick" delegation, an open pull request, or passing CI is never approval.
4. **Planning is not permission to build.** A request to plan, review, or investigate is read-only until I approve an implementation plan.
5. **No claim without evidence.** An agent may not say a review, test, or approval happened unless it actually did.
6. **Preserve what's approved.** Agents don't silently change scope, design, branding, or existing functionality.

---

## Roles and Separation of Duties

Each model has a defined lane, so no single agent defines the work, builds it, and grades it.

| Role | Held By | Responsibilities |
|---|---|---|
| **Owner and Final Authority** | Me (human) | Priorities, spend, approvals, merges, production deployments, releases |
| **Strategy and Product Architect** | ChatGPT | Product concepts, requirements, acceptance criteria, design direction, reviewing finished work against the vision |
| **Operations Orchestrator** | Claude | Coordinates the work, maintains handoff documentation, prepares review packages |
| **Engineering Execution and Verification** | Claude Code, Codex | Implementation, testing, and independent verification passes |

**The human is the only bridge between models.** Models don't communicate directly. When one model's work needs another's review, the orchestrator prepares a portable review package and I hand it across myself. I see everything that moves between them.

---

## The Three-Pass Workflow

Every significant piece of work moves through three passes. Each pass ends at a human decision point.

**Pass 1: Plan and Approve.** Scope, architecture, design, acceptance criteria, and risks are set before any code is written. I approve the design before implementation begins.

**Pass 2: Build and Validate.** A supervising agent coordinates implementation across specialist agents. An independent agent that didn't build the work then reviews the result against the Pass 1 acceptance criteria.

**Pass 3: Release Decision.** The agents present one consolidated go/no-go recommendation with its evidence. I make the final approval.

The structure separates the agent that builds from the agent that checks, and it fixes the definition of "done" in Pass 1, before anyone has an incentive to redefine it.

---

## Approval Gates

These actions always require my explicit, specific approval, even inside an approved plan:

- Merging pull requests
- Production deployments
- Database migrations
- Billing and payment changes, and refunds
- Authentication, permissions, and entitlements
- Destructive data changes
- Adding new providers, subscriptions, or paid APIs

Agents should flag risky changes before making them, not after.

---

## Evidence Standard

Every report that reaches me must state:

- **What changed**
- **What was tested**, including responsive layouts, interactions, integrations, and regressions
- **What passed**
- **What failed**
- **What remains unresolved**

Significant work also carries structured handoff documentation: decisions, progress, screenshots, test results, and open questions. Reports must keep separate repositories, and their CI results, clearly distinguished, so a pass in one is never presented as a pass in another.

---

## Keeping Oversight Usable

Oversight that buries the human in questions fails too, because the human starts approving without reading. So:

- Agents resolve routine technical findings themselves and bring **one consolidated decision per pass**.
- Agents don't invent new approval gates beyond the ones defined above.
- Recurring corrections are identified from history and fixed at the source, so I don't have to repeat the same feedback.

---

## Case Study: ThreadLane

ThreadLane is an AI-powered dealflow platform for B2B sales, coaching businesses, and real estate investors. It was built entirely by AI coding agents under this protocol and launched publicly in 2026 as a subscription product.

Examples of the protocol in practice:

- **Human-in-the-loop by design.** ThreadLane finds and qualifies prospects but performs **no automatic outreach**; the user decides who to contact.
- **No covert tracking.** The distribution features use campaign-level attribution, with no fingerprinting or hidden tracking.
- **Billing validated safely.** Payment flows are tested in a sandbox and with automated tests, never through live purchases.
- **Bounded spend.** Test infrastructure for one integrated build was capped at $5.
- **Gated release.** Plans were approved pass by pass; merges, production migrations, and deployment each required a separate final approval.

More: [stratomtechnologies.com/products](https://stratomtechnologies.com/products)

---

## Open Questions

Running this protocol daily has raised questions I can't yet answer rigorously, and they're the ones I most want to study:

- How often do agent self-reports diverge from what actually happened, and what kinds of divergence are most common?
- Which structures catch which failures: independent verifier models, required evidence, or human approval at specific gates?
- Where does human oversight break down as agents become more capable and the human understands less of the underlying work?
- How do you keep oversight strict without fatiguing the human into rubber-stamping?

---

## Contact

- LinkedIn: [linkedin.com/in/jeremiah-grey-881566187](https://www.linkedin.com/in/jeremiah-grey-881566187)
- Web: [stratomtechnologies.com](https://stratomtechnologies.com)
