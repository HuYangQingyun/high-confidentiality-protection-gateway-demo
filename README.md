# HCPG: High-Confidentiality Protection Gateway: Play Demo

Lightweight Protection Framework for Highest-Confidentiality Data and High-Value Assets. An independent framework for protecting core data. HCPG stands for High-Confidentiality Protection Gateway. Its protection scope is highest-confidentiality data and high-value assets, as the subtitle states.

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

## Either host works

On the screen, the host box is one box split in two: HAS-Core on top,
a horizontal line with "or" in the middle, and a generic framework below.
Tap either half to pick that host. The meaning is deliberate: you can use
our HAS-Core framework, or you can keep a generic framework you already
use. Either way, the request goes through the same gateway, and the gateway
answers the same way: allow, hold, or not core area. The host keeps its own
framework unchanged. It only asks the gateway before executing a core access,
and it obeys the answer. No host is favoured, and no generic framework is
named.
- Behaviours you can play with: normal core access, non-core access,
  tampered request, reused request, high-value direct transfer (held),
  emergency close, simulated authorised recovery, protected shutdown in two
  modes, authorised service resumption, restart, and the protected asset
  registry.
- Two different states that must not be confused: emergency close (gate stays
  on, everything held, survives restart, only an authorised recovery reopens
  it) versus shutdown (gate off, only a full authorisation switches it off).
  Restart never brings either state back on: a shut-down service needs its
  own authorisation to resume, and an emergency-closed gate needs an
  authorised recovery. Gate off never opens the vault: during shutdown
  the vault stays locked and unauthorised access is still refused.

## Recovery after an emergency close

Recovery is not one click. After an emergency close, an admin first requests
a reset, which starts admin verification. Only after verification passes does
an authorised recovery reopen the gate, and the recovery is recorded. Until
then the gate stays locked, including across a restart. In this demo the
verification step is simulated: the button reads "Simulate authorised
recovery" so no one mistakes the HTML page for real credential verification.

## Protected shutdown: two modes

A protected shutdown needs every approver, never one person alone:

- Autonomous mode: two customer officers approve, both inside the customer.
- Joint management mode: the customer owner and the vendor approve together.

Only when all approvers have approved does the gate enter a controlled
shutdown. A shutdown is a controlled stop of the gate, not a release of the
protected assets.

Device restart and service resumption are different things. After a
shutdown, restarting the device alone never resumes the service. Resumption
needs its own authorisation, from the same approvers, before the gate opens
again. The same holds for an emergency close: a restart never unlocks it.

Mode selection in the demo is a presenter tool only, labelled "Presenter:
mode ...". A real deployment mode change needs approval through the existing
authorisation mechanism. An ordinary admin cannot switch the authorisation
regime alone.

## Protected asset registry

The customer designates the protected assets at deployment: asset
identifiers, classification, and protection status. The gateway holds object
identifiers only. It never reads content. Registry changes go through the
deployment process only, never through a runtime click. The registry in this
demo is a static display only. It does not provide a real submission or
modification interface, and must not be taken as evidence that the interface
is complete.

## High-value direct transfer

A direct transfer over the example threshold is held first, the alarm is
raised, and independent manual verification is required before any decision.
Threshold values in the demo are illustrative only, not a customer configured
threshold.

## Audit

By default the audit is exception-only: normal allowed requests are
deliberately not written to the audit log. Only abnormal events appear
there. The customer may instead choose, at deployment, to enable a full
audit stream. That full stream is delivered to the customer's own system,
and the gate itself does not store it. The choice is made at deployment
startup on the customer's explicit request; it cannot be switched on during
runtime.

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
   `git commit -m "HCPG play demo"`,
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
