# High-Confidentiality Protection Gateway: Play Demo

Lightweight Protection Framework for Highest-Confidentiality Data and High-Value Assets. An independent framework for protecting core data. Full name: High-Confidentiality and High-Value Asset Protection Gateway.

This demo shows **what it does, not how it works**. The gate is a black box:
you see its answer (allow, hold, or not core area) and never its internals.
All data in the demo is simulated.

## What it shows

- One narrow interface: before executing a core access, a host framework asks
  the gate one question and obeys the answer. The host keeps its own framework
  unchanged.
- The same interface plugs into two hosts: our HAS-Core framework (native
  connection) and a generic framework (simulated, through a thin adapter that
  translates the one gate question into the host's own hook). The gate itself
  does not change, and no host internals are inspected or revealed.
- Behaviours you can play with: normal core access, non-core access,
  tampered request, reused request, emergency close, admin reset, joint
  shutdown (owner plus vendor), and restart.
- Two different states that must not be confused: emergency close (gate stays
  on, everything held, survives restart, only an admin reset reopens it) versus
  shutdown (gate off, only a joint authorisation switches it off, restart
  brings it back on).
- Exception-only audit: normal allowed requests are deliberately not written
  to the audit log. Only abnormal events appear there.

## What it does NOT show

No logic, no structure, no real code, no real keys, no internal decision
procedure, and no vendor names. Decisions in this demo are illustrative
scenarios. This is not a security product and not a certification.

## How to play

No build, no server, no install. Open `index.html` in any browser and press
the scenario buttons. Or publish it with GitHub Pages (below) and share the link.

## How to publish on GitHub

1. On GitHub, create a new repository (for example `high-confidentiality-protection-gateway-demo`).
   Do not add a README, license, or .gitignore from GitHub's templates if you
   upload these files, or you will get a merge conflict.
2. Upload `index.html` and this `README.md` to the repository (web upload
   works: Add file, Upload files, drag both files in, Commit).
   Or, from a terminal inside this folder:
   `git init`, `git add index.html README.md`,
   `git commit -m "High-Confidentiality Protection Gateway play demo"`,
   `git branch -M main`, `git remote add origin <your repository URL>`,
   `git push -u origin main`.
3. Enable Pages: repository Settings, Pages, Build and deployment, Source:
   Deploy from a branch, Branch: main, Folder: / (root), Save.
4. Your demo will be live at `https://<your GitHub username>.github.io/<repository name>/`
   within a minute or two.

## Production note

Production use requires laboratory validation, real identity and device
checks, real hardening, and a real deployment process. None of that is shown
or implied by this demo.
