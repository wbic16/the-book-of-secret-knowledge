# PATCHES.md — divergence from upstream

This repo is a fork of [trimstray/the-book-of-secret-knowledge](https://github.com/trimstray/the-book-of-secret-knowledge).
This file is the complete record of how the fork differs from upstream, so any
future upstream sync can re-apply the divergence cleanly.

**Fork point:** upstream `master` @ `7d37069a361d3fd9f214480755f7969744e866fa`
(the fork's tip was identical to upstream before this patch set).

## Patch set 1 — Wavelets 1–2 revision (2026-11-15)

Direction: Will Bickford, 2026-11-15 — "read and revise
https://github.com/wbic16/the-book-of-secret-knowledge based upon what we've
learned in the last two weeks." The last two weeks (Wavelets 1–2, Nov 1–14,
2026, plus the fleet work of Nov 15) produced verified, load-bearing lessons;
the ones that belong in a public knowledge compendium are added below, in the
book's own format (link + one-line description). Every added URL was fetched
and verified live on 2026-11-15. Task record: 24.5.16/8.7.12/5.5.8 in
tasks.phext.

All changes are additive. Nothing upstream was edited, moved, or removed.

### README.md

1. **Table of Contents** — one line added after the Shell Functions entry:
   `- **[Exocortex and Fleets](#exocortex-and-fleets-toc)**`
2. **CLI Tools → Network** — one entry appended (after mRemoteNG): Tailscale.
   The entry carries the fortnight's NFS lesson: Tailscale's 100.64.0.0/10
   range must appear in NFS exports and firewall allowlists, or mounts fail
   for no visible reason (the ranch's shared-cache rollout hit exactly this:
   a hardcoded server name resolved to a tailnet address outside the export
   list, and eight nodes were denied until the exports were widened).
3. **CLI Tools → Productivity** — one entry appended (after taskwarrior):
   ccusage. The token-accounting lesson: subscription dashboards report a
   percentage of a usage window, never tokens; the countable record is the
   local session logs (API consoles are the exception — they keep exact
   per-day token history).
4. **CLI Tools → Other** — two entries appended (after bed): sccache and
   Icecream, the distributed-build pair rolled out across the ranch fleet
   (one shared sccache cache served over NFS — a warm rebuild of
   phext-lattice ran 8.7 s with 97/97 cache hits — with an icecc scheduler
   on the hub node farming out compilation).
5. **New final chapter "Exocortex and Fleets"** appended at end of file —
   three subsections, twelve entries:
   - *Phext* (6): phext.io, libphext-rs, SQ, phext-lattice, edit.phext.io,
     phext-shell — the toolchain behind the fortnight's work. The
     libphext-rs entry carries the standing rule that phext is parsed
     through the reference implementation, never a hand-rolled parser
     (learned the hard way: seven hand-rolled parser versions in qexo,
     invisible because every test only ever read files qexo itself wrote).
   - *Fleet operations* (2): exocortical (the fleet provisioning tree; its
     entry carries the duty-cycle/thermal law for sustained work on
     thermally limited mini-PCs — hold the temperature band by freezing and
     resuming the load, never run hot) and qexo (the fleet orchestrator;
     its `distributed-builds` command performs the rollout in entry 4).
   - *Claims vs measurement* (4): the METR randomized trial (experienced
     developers 19% slower with AI on their own repos, believing themselves
     20% faster), the Copilot controlled experiment (arXiv:2302.06590,
     55.8% faster on a greenfield task), Anthropic's recursive
     self-improvement report (8× merged lines/day, with the author's own
     overstatement warning), and Garry Tan's LOC-controversy defence (the
     claims side, with its deflation math). These are the load-bearing
     references on both sides of the AI-productivity question, against
     which the Exocortex's own git-telemetry baseline was read
     (≈3,202 net code lines per active hour, sustained over Wavelets 1–2,
     measured across all 196 wbic16 repos).

### PATCHES.md

6. **This file** — new at the repo root; part of the divergence by design.

### Re-applying after an upstream sync

Cherry-pick the patch-set commit, or re-insert by anchor: the ToC line after
the Shell Functions line; Tailscale after the mRemoteNG entry; ccusage after
the taskwarrior entry; sccache/Icecream after the bed entry; the chapter at
end of file. If upstream adds any of these tools first, drop the duplicate
from this patch set and note it here.
