# Living Proof

*Show, don't claim: user guides recorded from your end-to-end tests.*

<!-- DRAFT 1, written from the voice note. Not for publishing yet. -->

> This is how I verify my apps nowadays: I don't read the code. I watch it work.

[GIF: one scenario playing beside its Gherkin, each line lighting up as it plays]

**See it live:** [BaconReader patches user guide](https://joancomasfdz.github.io/baconreader-morphe-patches/)

---

## Why I needed this

I patch an Android app. I change code I didn't compile, in an app I don't own, and I let an AI write most of the
changes. How do you test that?

You can't read your way to confidence. The AI writes code faster than I can review it, and "done, the tests pass" is a
claim, not proof. What I actually want to know is simple: does the feature do what we agreed, on a real screen?

So I stopped reading the code and started watching it work. Here is how it's built, one block at a time.

## Block 1: Ask me what's missing, don't grill me

Every repo has a set of instructions for the AI. The first one: whenever I ask for something, look at the code, look
at what I said, and ask me about the gaps. Contradictions, things I must decide, or something we've never done before
and you want to know how I want it.

Only that. I don't want a questionnaire. Two or three good questions, and we move on.

## Block 2: Say exactly what the app should do

Then the AI shows me how it will prove the feature works, as Gherkin: Given, When, Then.

I have a whole file on how to write a Gherkin. The language is precise: on this screen, tap this button, this text
shows. The texts are copied from the screen, never from the code. Anyone could pick up the Gherkin and play it on the
phone with nothing left to guess.

```gherkin
[a real Gherkin from the patches]
```

## Block 3: A place where the app can really run

This is where I invested the most.

For a web page it's simple: open a browser with Playwright and click around. My app runs on a phone, so I have a real
phone, plugged into my NAS at home, reachable only through my own private network. Next to it run fake versions of
the services the app talks to, like Reddit, so every test starts from the same state.

The AI can install the app, start it, change its settings, reset it and open it again, on its own. And because all of
it works from a cloud session, I can do everything from my phone.

It took a lot of work to make it fast, isolated and reliable. That work is what everything else stands on.

## Block 4: One Gherkin, one test, no translation layer

Each Gherkin becomes exactly one end-to-end test in C#. It holds the Gherkin word for word and does what each line
says, in order.

You might say: "That's what SpecFlow is for." It isn't, for me. SpecFlow needs a layer in between: small, disconnected
functions that match your sentences. And everyone writes their sentences their own way. "When the simulator is
loaded", "when the simulator is ready", "when the simulator is configured"... and instead of agreeing on one language,
you end up with a pile of regexes for the same step.

With an LLM, that layer is gone. I have three plain Markdown files:

1. how to write a Gherkin,
2. how to write an end-to-end test,
3. how to turn one into the other, line by line.

That's it.

```csharp
[one real test from the patches, short]
```

## Block 5: Green, recorded, posted

Here's the honest part: I often don't read the Gherkin when it's proposed. I say "go ahead". Because the rest of the
rules take care of it:

- you write the Gherkin, so you write its test;
- you run it, and it has to pass;
- when it's green, you record it on the phone;
- you open a pull request, and post the recordings on it: a GIF to watch right there in the comment, and an MP4.

It might take two hours. I don't care. When it's done, I open the PR and there's the Gherkin and the app doing it.

## Block 6: The video and the Gherkin, in sync

A GIF wasn't enough. While it records, the test also notes the moment each line of the Gherkin starts. A small player
puts the Gherkin on the left and the video on the right. Press play and the line being played lights up. Click a line
and the video jumps there.

You don't watch a video. You follow a script, line by line, and see each one happen.

## Block 7: One video per feature

Most people write many short tests, each checking one small thing. I went the other way: one feature, one scenario
that plays the whole of it.

Take "embed images in comments", with a setting to turn it on or off. Off, you see a link. On, the image loads. That's
one feature, so it's one video that shows both. Some of mine run seven minutes.

Why? Because that's what a training looks like. If someone sat next to you to show you a feature, they wouldn't
cut it into twelve clips.

## Block 8: The user guide builds itself

So now I had a Gherkin, a recording and a short page for every feature. That's a user guide.

After every merge, the pipeline puts them together into one page: each feature, what it does, and its newest
recording playing next to its Gherkin. Nobody writes it, and it can't go stale, because it is the tests.

When someone on Reddit asks how something works, I send them the guide: "this is how it works."

## Block 9: Then I kept going

- **Installing and updating** are recorded too, so the guide starts with how to get the app.
- **A VS Code extension**: open a test, click "Play", and the Gherkin and its video open next to the code.
- **The extension has its own recorded tests**, so the extension shows how it works the same way.

## What my job is now

I describe what I want. I answer two or three questions. I say "go ahead, don't bother me until the video is done."

Then I watch the video and read the Gherkin, and I say one of three things:

- "That's not how I want this Gherkin written."
- "That's not how I expected this to work."
- "Excellent job, merge."

I'm not testing the app anymore. The tests do. I don't read a plan, understand it and criticize it. If the code isn't
what I wanted, I'll see it in the app.

## "But what about performance? Security?"

Fair questions. They're not arguments against this; they're the next blocks. For performance I'd do the same thing:
an environment that measures it, runs every night, gathers the evidence and shows me what got better or worse. I'd
look at the results, not the code.

And to be clear: this is how I build my own apps. At work, I still read the code.

## Use it yourself

- The rules: [writing Gherkins] · [writing end-to-end tests] · [Gherkin to test, one to one]
- How I architect the end-to-end tests: its own article, coming next.

---

*Living Proof is how I build [BaconReader patches](https://github.com/JoanComasFdz/baconreader-morphe-patches).*

---

Licensed under [CC BY 4.0](LICENSE).
