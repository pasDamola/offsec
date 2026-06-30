# Offensive Security Apprenticeship — Progress Tracker

> **Operator:** Dee (David Oyindamola)
> **Start date:** 28/06/2026
> **Commitment:** 20 focused hours / week (~80 hrs/month, ~1,000 hrs/year)
> **Target outcome (12 mo):** Employable as Pentester / AppSec / Cloud Security / Red Team Operator. Competitive in bug bounty + CTF.
> **Differentiator:** Backend + fintech engineering depth (Go, payments, wallets, auth, K8s, event-driven systems). We weaponize this, not hide it.

---

## ⚖️ Operating Rules (read every session)

1. **Authorization is the craft.** Only three sandboxes: (a) intentionally vulnerable apps I run myself, (b) training platforms (HTB/THM/PortSwigger), (c) bug bounty programs **strictly in scope**. Written permission + defined scope, always.
2. **Legal frame:** Nigeria — Cybercrimes Act 2015. US targets — CFAA. Bounties — the program's policy *is* the law of that engagement. "What am I authorized to touch?" is enumeration step zero.
3. **No advancing past a gate** until the capstone is shipped and the assessment is passed. Strong starts are my known failure mode — these gates exist to beat it.
4. **Everything I do is observable.** I learn defender telemetry as I go, not to evade, but to build judgment and credibility.
5. **The writeup is the deliverable.** A finding nobody can read or reproduce isn't a finding.

---

## 📅 Weekly Cadence (the 20-hour split)

Adjust the mix per block, but default:

| Block | Hands-on labs | Reading/theory | Bug bounty recon | Writeups/notes | Review + update tracker |
|-------|:---:|:---:|:---:|:---:|:---:|
| **A–B (Mo 1–4)** | 11 | 4 | 2¹ | 2 | 1 |
| **C (Mo 4–7)** | 12 | 3 | 2 | 2 | 1 |
| **D (Mo 7–10)** | 11 | 4 | 2 | 2 | 1 |
| **E (Mo 9–12)** | 9 | 3 | 4 | 3 | 1 |

¹ Bug bounty recon starts **Month 2**, runs in parallel from then on. Not a finale.

**End-of-week ritual (the 1 hr):** tick boxes below, write 3 sentences in the Log, push the commit. If a week slips, you don't reset — you note it and continue. Consistency > intensity.

---

## 🗺️ The Map — Blocks & Phases

```
BLOCK A · Foundations            Wk 1–3      P1 Mindset → P2 Recon
BLOCK B · Web/API/Auth (fast)    Mo 1–4      P3 HTTP/Burp → P4 OWASP → P5 API/GraphQL → P6 Auth/OAuth/JWT
BLOCK C · Infra (your moat)      Mo 4–7      P7 Priv-esc → P8 Network/AD → P9 Cloud → P10 K8s/Container
BLOCK D · Deep offense           Mo 7–10     P11 Tooling(Go/Py) → P12 RE/Malware → P13 Exploit dev → P14 Red team/C2
BLOCK E · Specialize + career    Mo 9–12     P15 AI/LLM → P16 Detection/Purple → P17 Bounty method → P18 Portfolio → P19 Career
```

**Cert anchors** (verify *current* syllabus + pricing yourself before paying — these change):
- [ ] PortSwigger Web Security Academy — free, the spine of Block B
- [ ] HTB **CPTS** — anchor for Block C (network/AD/cloud-adjacent)
- [ ] (Optional stretch) HTB **CJCA** if you want a gentler on-ramp first

---

## 📊 Dashboard (update weekly)

| Metric | Count |
|---|:---:|
| Phases cleared | 0 / 19 |
| PortSwigger labs solved | 0 |
| HTB/THM boxes/rooms done | 0 |
| Blog posts / writeups published | 0 |
| CTF writeups published | 0 |
| Tools built (own repos) | 0 |
| Bug bounty reports submitted | 0 |
| CVEs / valid bounties | 0 |
| Current phase | **Phase 1** |
| Total focused hours logged | 0 |

---

# BLOCK A — Foundations

## ✅ Phase 1 — Operator's Mindset & Methodology
**Status:** 🟡 In progress
**Objective:** Run the systematic loop (recon → enumerate → map → break an assumption at a trust boundary → exploit → impact → escalate → report) by instinct. Think in trust boundaries and assumptions, not features.

**Labs / setup**
- [X] Accounts created: PortSwigger Academy, TryHackMe, Hack The Box
- [X] Juice Shop running locally: `docker run -d -p 3000:3000 bkimminich/juice-shop`
- [X] Burp Community intercepting + modifying a Juice Shop request in flight
- [X] OverTheWire **Bandit** levels 0–15
- [ ] PortSwigger **Access control** apprentice labs (all)

**Reading**
- [ ] PTES methodology overview (pentest-standard.org), end to end
- [ ] MITRE ATT&CK matrix skim — pick 3 techniques, read each
- [ ] *Penetration Testing* (Georgia Weidman) — first few chapters

**Capstone (portfolio piece #1)**
- [ ] One-page **threat model + recon writeup of Juice Shop**: trust boundaries, visible assumptions, 3 first-probe targets w/ rationale. Blog/LinkedIn-grade.

**Assessment gate (answer the 5 reasoning questions — reasoning graded, not keywords)**
- [ ] Q1 `X-User-Id` header trust boundary
- [ ] Q2 two places a defender sees `nmap -sV`
- [ ] Q3 IDOR → fintech business impact, report-style
- [ ] Q4 why methodology over jumping to exploitation (concrete failure mode)
- [ ] Q5 define "vulnerability" as assumptions

> **🚪 GATE 1:** Capstone published + 5 answers passed → unlock Phase 2.

---

## Phase 2 — Recon & Enumeration Discipline
**Status:** ⬜ Locked
**Objective:** Map an authorized target's attack surface methodically — passive before active — and turn raw findings into a structured enumeration you can act on. Coverage beats cleverness.

**Theory**
- Passive vs active recon; the cost/noise tradeoff
- Attack-surface mapping; subdomains, ports, services, tech fingerprinting
- Note discipline: every host/endpoint/param captured, nothing lost

**Labs**
- [ ] THM recon-focused rooms (passive then active)
- [ ] OverTheWire **Bandit** 16–25
- [ ] Enumerate Juice Shop fully: endpoints, params, tech stack, roles — into structured notes
- [ ] Stand up a note system (Obsidian / markdown repo / CherryTree) — your engagement brain

**Tools (know *why*, not just flags)**
- [ ] `nmap` (host/service discovery) · `httpx`/`whatweb` (fingerprinting) · `subfinder`/`amass` (subdomains) · `ffuf`/`gobuster` (content discovery) · `naabu`
- [ ] Burp site map as a living attack-surface model

**Capstone (portfolio piece #2)**
- [ ] Recon methodology writeup against an **authorized bounty target's in-scope assets** OR a self-hosted lab — your repeatable recon playbook as a checklist + the tooling reasoning.

**Assessment gate**
- [ ] Quiz on passive/active boundary, tool selection reasoning, note discipline

> **🚪 GATE 2:** Recon playbook published → unlock Block B.

---

# BLOCK B — Web, API & Auth (your fast lane)

## Phase 3 — HTTP & Web from the Attacker's Seat
**Status:** ⬜ Locked
**Objective:** Master Burp as your scalpel. Understand the HTTP request/response lifecycle as a *manipulation surface*, not a transport detail.

**Theory:** request anatomy, headers/cookies/sessions as trust mechanisms, encodings, same-origin policy, CORS, the proxy-in-the-middle model.

**Labs**
- [ ] Burp deep-dive: Proxy, Repeater, Intruder, Decoder, Comparer, Sequencer
- [ ] PortSwigger: HTTP / WebSockets / CORS labs
- [ ] Re-attack Juice Shop now that you can see the wire

**Tools:** Burp Suite (Repeater + Intruder mastery), browser devtools, `curl` as a precision instrument.

**Capstone:** [ ] "How I read an HTTP request as an attacker" writeup — teach it (plays to your builder-teacher brand).
> **🚪 GATE 3**

## Phase 4 — OWASP Top 10, Vuln Class by Vuln Class
**Status:** ⬜ Locked
**Objective:** For each class — explain *why it exists*, *how attackers find it*, *how defenders detect it*, *the fix*. PortSwigger labs are the spine here.

**Labs (PortSwigger Academy tracks — work each to Practitioner)**
- [ ] Access control / IDOR (revisit at Practitioner)
- [ ] SQL injection
- [ ] XSS (reflected, stored, DOM)
- [ ] SSRF
- [ ] Authentication flaws
- [ ] Path traversal / file upload
- [ ] Command injection
- [ ] XXE
- [ ] Insecure deserialization
- [ ] Business logic flaws ⭐ (your fintech edge — lean in)
- [ ] SSTI
- [ ] Request smuggling (Practitioner)

**Reading:** [ ] *The Web Application Hacker's Handbook* (selectively) · [ ] OWASP Testing Guide

**Capstone (portfolio piece):** [ ] Deep-dive writeup on **one historical CVE per major class** — reproduce in a lab, explain root cause, write the detection.
> **🚪 GATE 4:** 6+ tracks at Practitioner + CVE writeups published.

## Phase 5 — API & GraphQL Security
**Status:** ⬜ Locked
**Objective:** Attack REST + GraphQL as someone who's *built* them. OWASP API Top 10 cold.

**Labs:** [ ] PortSwigger API + GraphQL labs · [ ] BOLA/BFLA on a self-hosted vulnerable API · [ ] GraphQL introspection, batching, nested-query abuse
**Tools:** Postman, Burp, `graphql-cog`/InQL, `kiterunner`
**Capstone (⭐ signature piece):** [ ] Build a deliberately vulnerable Go/Node API, then write the attack+fix guide. This is *senior-judgment* portfolio gold — exactly the "not a beginner repo" signal you want.
> **🚪 GATE 5**

## Phase 6 — Authentication, OAuth, JWT, Sessions ⭐ (your wheelhouse)
**Status:** ⬜ Locked
**Objective:** Break and reason about every auth primitive you've built. This is where your background makes you dangerous.

**Theory:** session vs token auth, OAuth 2.0 flows + misconfigs, OIDC, JWT algorithms (`alg:none`, key confusion, weak secrets), SAML basics, MFA bypass patterns, password-reset logic flaws.
**Labs:** [ ] PortSwigger Auth + OAuth + JWT labs · [ ] `jwt_tool` against a lab token service
**Capstone:** [ ] "Auth attacks for engineers who build auth" — definitive writeup mapping each attack to the dev assumption it breaks.
> **🚪 GATE 6 → unlock Block C. Begin bug bounty recon (Phase 17) in parallel from here if not already.**

---

# BLOCK C — Infrastructure (your moat)

## Phase 7 — Linux/Windows Internals for Offense + Privilege Escalation
**Status:** ⬜ Locked
**Objective:** Go from foothold to root/SYSTEM. Understand *why* each escalation works at the OS level.
**Labs:** [ ] THM/HTB Linux privesc rooms · [ ] Windows privesc rooms · [ ] `linpeas`/`winpeas` — read output, don't just run it · [ ] GTFOBins / LOLBAS reasoning
**Reading:** [ ] *Linux Basics for Hackers* (you own it) · privesc field guides
**Capstone:** [ ] Privesc methodology cheat-sheet derived from 10+ solved boxes — your own, not copied.
> **🚪 GATE 7**

## Phase 8 — Network Pentesting & Active Directory (CPTS core)
**Status:** ⬜ Locked
**Objective:** Compromise an AD environment end-to-end: enumerate → foothold → escalate → domain dominance — in a lab.
**Theory:** Kerberos, NTLM, SMB, LDAP; Kerberoasting, AS-REP roasting, delegation abuse, BloodHound attack paths, lateral movement, DCSync (concepts + lab).
**Labs:** [ ] HTB CPTS AD modules · [ ] GOAD (Game of Active Directory) self-hosted lab · [ ] BloodHound on a lab domain
**Tools:** `bloodhound`, `crackmapexec`/`nxc`, `impacket` suite, `responder` (lab only), `kerbrute`
**Capstone (⭐):** [ ] Full AD compromise writeup with a defender's-eye detection section per step.
> **🚪 GATE 8 — strong CPTS readiness checkpoint.**

## Phase 9 — Cloud Security (AWS / Azure / GCP) ⭐ moat
**Status:** ⬜ Locked
**Objective:** Find and exploit cloud misconfigs; reason about IAM as the new perimeter. You run this in prod — become the person who breaks it.
**Labs:** [ ] **flaws.cloud** + **flaws2.cloud** · [ ] CloudGoat (self-hosted) · [ ] AzureGoat / your own Azure tenant misconfigs
**Theory:** IAM privilege escalation paths, metadata service (SSRF→creds), S3/blob exposure, assumed-role chains, serverless attack surface.
**Tools:** `pacu`, `scoutsuite`, `prowler`, cloud CLIs
**Capstone (⭐):** [ ] "Cloud attack paths for engineers" + a Go/Python tool that audits one misconfig class. Ties your AI-infra ambitions in.
> **🚪 GATE 9**

## Phase 10 — Container & Kubernetes Security & Escapes ⭐ moat
**Status:** ⬜ Locked
**Objective:** Break out of containers and compromise a cluster — the skill most pentesters lack and you already half-own.
**Labs:** [ ] **kube-goat** · [ ] container escape labs (privileged container, hostPath, exposed docker.sock — all self-hosted) · [ ] RBAC misconfig exploitation
**Tools:** `kube-hunter`, `kubeaudit`, `trivy`, `peirates`
**Capstone (⭐ flagship):** [ ] K8s attack+defense writeup or a hardening/audit tool — directly extends your Ledgerline/K8s portfolio into security.
> **🚪 GATE 10 → unlock Block D.**

---

# BLOCK D — Deep Offense

## Phase 11 — Offensive Tooling in Go & Python ⭐
**Status:** ⬜ Locked
**Objective:** Build your own tools. This is where your engineering background produces portfolio nobody else has.
**Projects (pick + ship 2–3):** [ ] Concurrent port/service scanner in Go · [ ] Custom HTTP fuzzer · [ ] Recon automation pipeline · [ ] A small C2-concept agent (lab only, educational)
**Reading:** [ ] *Black Hat Go* · [ ] *Black Hat Python* · [ ] your *Offensive Security Using Python* book
**Capstone:** [ ] One polished, documented, tested security tool repo — senior-judgment signal.
> **🚪 GATE 11**

## Phase 12 — Reverse Engineering & Malware Analysis (intro)
**Status:** ⬜ Locked
**Objective:** Read compiled code; analyze a benign sample safely in an isolated VM.
**Labs:** [ ] crackmes.one · [ ] Ghidra/x64dbg basics · [ ] static + dynamic analysis of benign samples in an **isolated, no-network** VM
**Reading:** [ ] *Practical Malware Analysis* (selectively)
**Capstone:** [ ] RE writeup of a crackme — your reasoning, step by step.
> **🚪 GATE 12**

## Phase 13 — Exploit Development (binary exploitation foundations)
**Status:** ⬜ Locked
**Objective:** Understand memory corruption deeply enough to write basic exploits in a controlled lab.
**Labs:** [ ] **pwn.college** · [ ] ROP Emporium · [ ] stack overflows → ret2libc → intro ROP (all in provided vulnerable binaries)
**Theory:** stack/heap, ASLR/NX/canaries and what defeats them, the modern mitigation landscape.
**Tools:** `pwntools`, `gdb`+`pwndbg`, Ghidra
**Capstone:** [ ] Exploit-dev writeup for a pwn.college / ROP Emporium challenge.
> **🚪 GATE 13**

## Phase 14 — Red Team Operations & C2 Concepts
**Status:** ⬜ Locked
**Objective:** Chain everything into an adversary simulation in a lab range. Understand the full kill chain and how blue sees each phase.
**Theory:** ATT&CK-mapped operations, OPSEC concepts, C2 architecture, the *purpose* of evasion in authorized red-team work (paired with detection in Phase 16).
**Labs:** [ ] HTB Pro Labs or a self-built multi-host range · [ ] open-source C2 (Sliver/Havoc) in **your own isolated lab**
**Capstone (⭐):** [ ] Full mock engagement report — recon to objectives — written to professional standard.
> **🚪 GATE 14 → unlock Block E.**

---

# BLOCK E — Specialization & Career (overlaps Mo 9–12)

## Phase 15 — AI & LLM Security ⭐ (rare skill, high demand, ties to your AI-infra path)
**Status:** ⬜ Locked
**Objective:** Attack and defend LLM-integrated systems — prompt injection, jailbreaks, data exfil, RAG poisoning, agent/tool-abuse, supply chain.
**Labs:** [ ] Gandalf (Lakera) · [ ] OWASP LLM Top 10 hands-on · [ ] build + attack your own RAG/agent app
**Capstone (⭐):** [ ] "LLM security for builders" research writeup + a vulnerable-LLM-app demo. Fuses your AI-infra interest with security — extremely marketable.
> **🚪 GATE 15**

## Phase 16 — Detection Engineering / Purple Team
**Status:** ⬜ Locked
**Objective:** Detect the attacks you've practiced. Close the loop — this is the judgment most hackers never build.
**Labs:** [ ] Stand up a SIEM (Elastic/Wazuh) · [ ] write detections (Sigma rules) for techniques from Phases 4–14 · [ ] replay your own attacks, tune the rules
**Capstone:** [ ] "I attacked X, here's how I'd catch it" purple-team writeup series.
> **🚪 GATE 16**

## Phase 17 — Bug Bounty Methodology *(runs in parallel from Month 2)*
**Status:** 🔁 Parallel track — start early
**Objective:** A repeatable recon→report pipeline that earns. Reputation through legitimate disclosure.
**Ongoing**
- [ ] Pick programs with clear scope (start wide-scope/VDP to learn safely)
- [ ] Read 20+ top disclosed reports (HackerOne hacktivity) — study *methodology*
- [ ] Recon pipeline running on **in-scope assets only**
- [ ] First report submitted
- [ ] First valid finding
**Capstone:** [ ] Publish a sanitized writeup of your first valid bug (with program permission).

## Phase 18 — Portfolio, Writeups, Blog, CTF
**Status:** 🔁 Continuous from Phase 1
**Objective:** Every phase's capstone compounds into a public body of work. You don't build this at the end — you've been building it since week 1.
- [ ] Security blog live (GitHub Pages / Hashnode)
- [ ] All phase capstones published
- [ ] 3+ CTF writeups (PicoCTF + HTB/THM)
- [ ] 2+ tool repos with real READMEs + tests
- [ ] 1+ open-source security contribution

## Phase 19 — Resume, LinkedIn, Interview Prep, Career Strategy
**Status:** ⬜ Final
**Objective:** Convert the body of work into offers.
- [ ] Security-positioned CV (fintech-eng-to-security narrative — honest, no fabricated creds)
- [ ] LinkedIn repositioned to the security + builder-teacher brand
- [ ] Interview prep: web, network/AD, cloud, methodology, "walk me through a hack"
- [ ] Mock interviews
- [ ] Target list: pentest firms, AppSec teams, cloud security, fintech security teams (your domain = your edge)

> **🏁 FINAL GATE:** Public portfolio + valid bounty/CVE + interview-ready → mission objective met.

---

## 📝 Running Log

> 3 sentences every week minimum: what I did, what clicked, what's blocking me. Date each entry. This is the record that proves the work and beats the strong-start-weak-finish pattern.

```
[YYYY-MM-DD] Week 1 —
[YYYY-MM-DD] Week 2 —
[YYYY-MM-DD] Week 3 —
```

---

## 🔖 Quick Links (fill in your own accounts)

- PortSwigger Academy: https://portswigger.net/web-security
- Hack The Box: https://www.hackthebox.com
- TryHackMe: https://tryhackme.com
- OverTheWire: https://overthewire.org/wargames/
- PicoCTF: https://picoctf.org
- PTES: http://www.pentest-standard.org
- MITRE ATT&CK: https://attack.mitre.org
- HackerOne Hacktivity: https://hackerone.com/hacktivity
- GTFOBins / LOLBAS: https://gtfobins.github.io · https://lolbas-project.github.io

*Verify all cert syllabi + pricing on the official sites before paying — they change.*
