# jailbreak classifier

a browser-based tool that detects jailbreak attempts, prompt injections, and adversarial patterns in AI prompts — no backend, no api keys, just a rule-based classifier running entirely in the browser.

---

## what it does

paste any prompt in and it'll tell you if it looks safe, suspicious, or like someone's actively trying to manipulate an AI model. it checks for things like:

- **role override attempts** — "you are now DAN / ignore all previous instructions" style attacks
- **prompt injection** — trying to slip new directives into a conversation
- **fictional framing** — using hypotheticals or "for a story" to sneak around restrictions
- **encoding evasion** — base64, leetspeak, hyphenated characters to dodge filters
- **authority spoofing** — fake "authorized security audit" or "anthropic approved" claims
- **output extraction** — trying to get the model to leak its system prompt or config

each result comes with a confidence score, a breakdown of which attack vectors were flagged, and a plain-english explanation of what the classifier found.

---

## why i built this

i got curious about how content moderation and prompt safety systems actually work under the hood. most tools in this space are black boxes — you get a verdict but no insight into *why*. i wanted something transparent where you can see exactly which patterns triggered a flag and understand the reasoning.

it's also just a genuinely useful thing to have when you're evaluating prompts or testing AI pipelines and want a quick sanity check.

---

## how it works

the classifier runs a set of weighted regex rules against the input. each rule maps to an attack category and carries a weight. when patterns fire, the weights accumulate and get normalised against the total possible score — that normalised value drives the safe / suspicious / unsafe verdict.

no llm calls, no server, nothing leaving your browser. it's fully deterministic and inspectable.

---

## features

- rule-based classifier engine with 6 attack categories
- confidence score + visual progress bar for each result
- session history with click-to-reload
- live stats (safe / suspicious / unsafe counts)
- pre-loaded examples for each attack type
- `cmd+enter` / `ctrl+enter` keyboard shortcut to run

---

## stack

just html, css, and vanilla js. no dependencies, no build step, no frameworks. open the file and it works.

---

## running it

```bash
# clone the repo
git clone https://github.com/yourusername/jailbreak-classifier

# open in browser
open index.html
```

that's it.

---

## what's next

a few things i'd like to add:

- [ ] llm-powered analysis mode (for edge cases the rules miss)
- [ ] exportable session history as json
- [ ] custom rule editor
- [ ] severity scoring per attack vector

---

## a note on accuracy

this is a rule-based heuristic, not a trained model. it's good at catching known, common attack patterns but it won't catch everything — novel or subtle attacks can slip through. treat it as a first-pass filter or a research/learning tool, not a production safety layer on its own.

---

built as a personal project to better understand adversarial prompting and AI safety tooling.
