# Living Proof

*Show, don't claim: user guides recorded from your end-to-end tests.*

<!-- DRAFT OUTLINE. Built from the ground up: each block rests on the one before it.
     The voice will follow the WhatsApp audio once it's pasted. -->

> This is how I verify my apps nowadays: I don't read the code. I watch it work.

[GIF: one scenario playing beside its Gherkin, each line lighting up as it plays]

**See it live:** [BaconReader patches user guide](https://joancomasfdz.github.io/baconreader-morphe-patches/)

---

## The problem

<!-- Why this exists. -->
- AI writes code faster than I can read it.
- "Done, tests pass" is a claim, not proof.
- What I actually want to know: does the feature do what we agreed, on a real screen?

## Block 1: Say exactly what the app does

<!-- The foundation: precise, plain language. -->
- A Gherkin (Given / When / Then) for each behavior.
- Written so anyone can play it on the device, with nothing left to guess: "on this screen, tap this button, this
  text shows".
- Texts copied from the screen, never from the code.
- A written set of rules for how to write one, so every Gherkin reads the same.

## Block 2: Agree before anything is built

<!-- Rests on 1: precise words make agreement possible. -->
- For every feature, the AI proposes the Gherkins first.
- We discuss them until they're right. Only then does any code get written.
- The Gherkins *are* the acceptance criteria.
- My job moves from "how" to "what".

## Block 3: One Gherkin, one test, word for word

<!-- Rests on 2: what we agreed becomes executable. -->
- Each Gherkin becomes exactly one end-to-end test.
- The test holds the Gherkin word for word and does what each line says, in order.
- Rules for writing the tests, and rules for translating a Gherkin into a test.
- Nothing extra, nothing missing: if it isn't in the Gherkin, the test doesn't do it.

## Block 4: Record it playing

<!-- Rests on 3: a test that follows the lines can mark them. -->
- The test runs on a real device (here: a phone next to my NAS) and records a video.
- It stamps the time each line of the Gherkin starts.
- Result: a video you can follow line by line, with each line highlighted as it plays.

## Block 5: Proof where the review happens

<!-- Rests on 4: the recording goes where decisions are made. -->
- The recordings are posted on the pull request, next to their Gherkins.
- Reviewing a feature means watching it work.
- A change after the recording means recording again: the proof is always current.

## Block 6: The user guide builds itself

<!-- The top of the stack. -->
- Each feature has a short page in plain words.
- After every merge, the pipeline builds the user guide from those pages and the newest recordings.
- Nobody writes the guide. It can't go stale, because it is the tests.

## What changes

<!-- Step back and show the whole stack. -->
- One agreement → a test → a video → a page of documentation.
- Trust comes from evidence, not from reading diffs.
- [Optional: the diagram of the stack, blocks 1 → 6]

## Where it stops

<!-- Honesty makes the rest credible. -->
- "Looks right" (colours, spacing) is still for a human eye, on the videos.
- It needs a real device and a recording pipeline: an upfront cost.
- [Anything from the audio]

## Use it yourself

- The rules: [writing Gherkins] · [writing e2e tests] · [Gherkin to test, one to one]
- The pipeline: [recording] · [posting on PRs] · [building the guide]
- [How to adapt it to a web app, a desktop app…]

---

*Living Proof is how I build [BaconReader patches](https://github.com/JoanComasFdz/baconreader-morphe-patches).*

---

Licensed under [CC BY 4.0](LICENSE).
