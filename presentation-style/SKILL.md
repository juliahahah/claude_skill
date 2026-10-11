---
name: presentation-style
description: "Apply this presentation style whenever creating slides, decks, or a PowerPoint/.pptx presentation — ESPECIALLY for technical or research talks, workshops, system walk-throughs, or any deck that explains how something works. Trigger this whenever the user asks to make/build/design a presentation, deck, or slides, even if they don't name a style. It layers a specific visual + writing style on top of the base pptx skill: light background, a top progress bar of chapters (current one highlighted, not-yet-reached ones faded), architecture diagrams built from official icons or the author's own figures, one-component-at-a-time spotlight reveals on a single unchanging diagram, plain and direct slide text in the audience's own technical terms (no metaphors, slogans, or filler lines), content kept strictly inside the scope the user asked for, and a deliberate avoidance of the tells that make slides look AI-generated. Use it together with the base pptx skill, not instead of it."
---

# Presentation Style

This skill is a **style layer**. The base `pptx` skill (`/mnt/skills/public/pptx/SKILL.md`) still owns *how* a `.pptx` gets generated, rendered, and QA'd — read it and use it for all the mechanics. This skill owns *what the deck should look and read like*. When both apply, follow the base skill's technical workflow and this skill's style rules.

The style comes from studying a strong technical workshop deck and from user feedback on generated decks. The goal is decks that a first-time listener can follow without getting lost or overwhelmed — and that don't look or read like they were auto-generated.

## The core idea

A good technical deck feels like a person walking you through a system, not a document dumped onto slides. Five habits create that feeling, and every rule below serves one of them:

1. **Anchoring** — keep one diagram on screen and move a spotlight across it, instead of flashing a new picture every slide. Listeners build one mental map instead of re-orienting constantly.
2. **Orientation** — a persistent progress bar so listeners always know where they are and how much is left.
3. **Credibility** — real official icons and the author's real figures, not improvised shapes or generic circles.
4. **Directness** — say what each thing is, in the terms the audience already uses, backed by real examples and numbers. No metaphor standing in for the real concept.
5. **Restraint** — a clean light layout, and nothing on a slide that doesn't carry information: no decorations, no recurring callouts, no slogans, nothing outside the requested scope.

---

## 1. Light background, restrained accent system

Use a **light background** (white `FFFFFF` or a very light neutral). Body text is **dark blue-grey (e.g. `1F2A37`), never pure black `000000`** — pure black on white is harsh to read.

Pick **one primary accent color + one secondary/emphasis color** for the whole deck, and use them with restraint:
- Primary accent: section titles, the active progress-bar chapter, the currently-spotlighted diagram element.
- Secondary/emphasis: a second logical group in a diagram, a key arrow, one stat you want to pop.

Do **not** make the deck one flat sheet of black-on-white — that reads as lifeless. The accent color is what keeps a light deck feeling alive. But resist using more than two accents; more colors read as noise, not design.

> Why not a dark background? A dark "stage" makes bright diagrams pop dramatically, but light decks read better in bright rooms, photograph and print cleanly, and match the native look of official icons (which are designed for white backgrounds). We deliberately trade a little drama for legibility.

---

## 2. Top progress bar (chapter orientation)

Put a **horizontal chapter bar across the top** of every content slide, listing the deck's main sections in order (e.g. `1. 研究流程　2. 第一週進度　3. 結論`).

- The **current chapter is highlighted** — solid fill in the primary accent, high-contrast text.
- **Chapters not yet reached are faded** — light tint / low-contrast text.
- Already-passed chapters can be a middle state (visible but muted) or the same faded style — pick one and stay consistent.

This is the *chapter-level* version of the spotlight idea in rule 4: at any moment, exactly one thing is lit and the rest recede. Keep the bar in the same position and size on every slide so it reads as a stable frame, not new content.

---

## 3. Architecture-diagram-driven, with official icons

Explain systems **through a diagram**, not through bullet lists. When a slide is about how pieces connect, draw the pieces and the connections.

**Icons must be real, official ones** — this is general, not AWS-specific. Whatever the technology (AWS, Azure, GCP, Kubernetes, Docker, React, ChatGPT/OpenAI, Postgres, anything with an official mark), get the genuine icon:

1. Find the official source and fetch the real file (SVG preferred, PNG ok). Examples of where to look: **AWS Architecture Icons**, **Azure / GCP official icon sets**, **kubernetes.io** and the CNCF artwork repo for k8s, a project's official brand/press page or GitHub for its logo.
2. Use vendor **standard colors** — they carry meaning and recognition (e.g. AWS DynamoDB purple, Lambda orange, S3 green).
3. **Never hand-draw or "generate" a brand logo.** A model-drawn logo comes out distorted, mis-colored, or simply wrong, and instantly looks fake. If the genuine icon truly can't be fetched, fall back to a **neutral generic shape** (a plain labeled box) and note that it's a stand-in — do not fake the brand mark.
4. **Never use a generic colored circle as a substitute for a real icon.** Rows of same-colored circles with a word inside are a classic AI-deck tell (see rule 10).

If you have web access, fetch icons during the build. If you don't, tell the user which icons you couldn't retrieve and used neutral boxes for, so they can drop the real files in.

For a **research talk**, the paper's own figures are the official diagrams: reuse them (cropped, spotlighted) instead of redrawing them, and keep their labels consistent with the slide text.

---

## 4. One-component-at-a-time spotlight reveal

This is the signature technique. When walking through a diagram with several parts, **do not swap in a new image per slide.** Instead keep the *same* diagram and move a spotlight across it, one slide per component.

Since `.pptx` has no live animation from this environment, simulate it with **a sequence of near-identical slides**:

- Slide *i* keeps the whole diagram in place.
- The **component being discussed is at full strength**: full color/opacity, plus a subtle highlight (a soft outline, a light tinted backing shape, or a gentle shadow).
- **Every other component is de-emphasized**: reduced opacity and desaturated toward light grey.
- Connecting lines/arrows into the active component can stay dark; unrelated ones fade with their components.

On a **light** background the highlight is "keep this element saturated while the rest go pale grey" — do **not** use a white outline as the highlight (it's invisible on white); use the accent color, a light tinted backing, or a soft shadow instead.

Keep positions identical across the sequence so nothing jumps — only emphasis changes. The listener's eyes stay put; only the spotlight moves.

---

## 5. Build complex diagrams up progressively

For a diagram that ends up busy, **don't reveal it fully formed.** Start from the simplest skeleton and add one piece at a time across slides, the way a person would draw it on a whiteboard while explaining.

Example rhythm for a client–server picture: two boxes → add the request arrow → add the response arrow → add the middle platform → add labels. By the last slide the full picture is built, but the listener assembled it with you and understands every part.

Use **color to separate logical groups** within a diagram (e.g. one leg of a round-trip in the accent color, the other leg in the secondary color) so a multi-step flow reads as distinct steps, not one tangled line.

---

## 6. No metaphors on slides — use the field's own terms

Don't build a deck around an analogy, and don't put analogies on slides. A metaphor carried through the talk, and especially a box repeating it on every slide, reads as AI-written: the listener has to translate the image back into the real idea, and the extra lines push out information.

- **No running analogy and no analogy callouts.** No theme that maps the system onto an everyday story (e.g. a cache explained all talk long as "a librarian keeping popular books at the front desk"), and no "比喻" box under each figure.
- **Don't rename technical concepts through a metaphor.** If the source says cache, hit rate, eviction policy, TTL, the slide says exactly that — not 圖書館員、櫃台、熱門書、借閱期限.
- **Don't add lines that only extend an image.** A line like 「圖書館員下班時會把櫃台清空」 (for "the cache is cleared on restart") is filler: state the fact once where it matters, or drop it if the figure already shows it.
- **Concreteness comes from real material** — a real example from the data, an actual number, the actual figure. That is what lets a listener picture the idea.
- Only when the user explicitly asks for an analogy: use it once, in the speaker notes or on a single slide, never as a recurring device.

---

## 7. Plain, direct slide text (no AI tone)

Slide text is written for someone hearing this for the first time, in the register of the presenter's own field, not as a generated summary. Understood-at-a-glance beats sounds-impressive, and neutral beats catchy.

Rules for on-slide wording (they apply to the speaker notes too):
- **Titles name the section or state the slide's point plainly.** 「動機」、「總結」、「問題②　TTL：所有資料共用同一個過期時間」. No hook or teaser titles (「一個看起來很簡單的問題」), no slogan titles (「三件事一起改」、「三個問題，三個解法」).
- **One idea per line.** Don't stack three concepts into one long clause with 透過…以…進而… chains.
- **Concrete over abstract.** A number, an example, or a picture instead of naming a concept: 「p99 延遲從 120 ms 降到 45 ms」 beats 「效能得以顯著提升」.
- **Short is not the same as clear.** Don't compress an argument into telegraphic fragments (「3×　流量尖峰時，快取有效容量的差距」、「調整 TTL 補不了冷資料的缺口」); the listener cannot rebuild the logic. Write each point as short complete sentences: what is done → what goes wrong → the consequence (「快取容量固定，而每個請求都會寫入快取；流量變成 3 倍時，每筆資料平均只能在快取裡停留原本三分之一的時間」).
- **Say what every number measures.** A big number is labeled with the quantity, not just the source: 「85%：快取命中率，也就是直接由快取回應的請求比例」, not 「85%　快取」.
- **Introduce a symbol or term before using it** (λ, TTL, p99, EMA), in plain words the first time it appears.
- **No coined translations of technical terms.** Keep the source's term or describe it plainly (「TTL（資料在快取中的存活時間）」、「近期平均」) instead of inventing a word the audience has to decode (「存活期限值」、「錨定」、「有效容量」).
- **Link each fix to the problem it solves with matching labels**: 「缺點 1 / 缺點 2」 on the problem slide → 「分層 TTL（解決缺點 1）」、「預熱（解決缺點 2）」 on the method slide.
- **Neutral, precise wording in the source's register.** A paper's talk uses the paper's terms in plain declarative sentences. No dramatizing colloquialisms: 「暗中多花 3 倍」→「成本增加 3 倍」, 「用到底」→「之後固定」, 「直接爆掉」→「超出容量」.
- **Keep the jargon the audience uses.** For a technical audience, don't paraphrase established terms into everyday words; use the term directly and explain it only if it is new.
- **No slogans or catchphrase closers** (「快、穩、省，一次到位」、「資料不對，架構再好也沒用」), and no catchy parallel triads invented for the slide.
- **No rhetorical questions as headings or punchlines.** 「為什麼大家都忽略了冷資料？」→「既有快取研究只評估熱門資料的命中率」.
- **Don't anthropomorphize the system or model.** 「快取覺得這筆資料很重要 → 留久一點」→「這筆資料的存取頻率高於平均 → TTL 加長」.
- **Every line carries information.** Don't restate what the figure already shows, and don't add transition or decoration lines.
- **Fewer words per slide is better** — cut repetition and decoration, never the reasoning. A slide is glanced at; detail goes in what you *say* (the speaker notes).

**When the user's source material is too thin to be concrete, ask for specifics** — a real example, a number — rather than filling the slide with abstract, professional-sounding filler or a metaphor. Good input is what lets the text stay concrete; inventing abstractions to cover a gap is exactly what produces hard-to-follow AI text.

---

## 8. Stay inside the requested scope

When the user scopes the deck — 「只講問題、動機、方法」, 「10 分鐘」, 「只要結果」 — every slide and every line stays inside that scope.

- **Don't add content the user didn't ask for**, even as a closing line: no results or headline numbers on the summary slide of a problem-and-method talk, no extra "future work" or "related work" section.
- **The summary recaps only what was presented.**
- **If something outside the scope seems important, say so in your reply** and let the user decide; don't put it in the deck.
- **Size the deck to the time budget** (roughly 45–60 s per content slide) and write the speaker notes to that length.

---

## 9. Stable layout frame

Give every content slide the **same skeleton** so listeners always know where to look:
- Top: the chapter progress bar (rule 2), same place every slide.
- A large slide title in a consistent position.
- Consistent footer (e.g. logo) and page number location.

A stable frame lowers cognitive load — listeners spend attention on your content, not on re-learning each slide's layout. Vary the *content area* layout between slides (see below) but keep the frame fixed. The frame holds orientation only: a content box that appears in the same slot on every slide (analogy, tip, takeaway) is template filler, not frame.

---

## 10. Avoid the AI-deck tells

These make a deck look auto-generated. Avoid them (several are also in the base pptx skill's Avoid list):

- **No decorative line under the title.** The single most recognizable AI-slide tell.
- **No decorative color bars / stripes spanning an edge** — no full-width header/footer color band, no vertical sidebar stripe, no thin accent stripe along a card edge. To set something apart use a subtle tint, a soft shadow, or an icon.
- **No leftover template/watermark cruft** — stray faded numbers, ghost placeholder text, meaningless decorative filler shapes. Clean them out.
- **No "title + three bullets" on every slide.** That form-filling rhythm is a giveaway; vary the layout — sometimes a diagram, sometimes a big number, sometimes a two-column compare, sometimes a single sentence.
- **No abstract adjective walls** — "高效、穩定、可擴展" with no example behind them. See rule 7.
- **No generic-blue-everything, no default gradient, no everything-centered.** Center titles only; left-align body text and lists.
- **No faded light arrows on a light background** — arrows and lines must be dark enough to read on white.
- **No hand-drawn/generated brand logos and no generic circles standing in for icons** (see rule 3).
- **No recurring callout strip** — an "analogy" / "takeaway" / "key point" box repeated on every slide.
- **No running analogy or metaphor-renamed concepts** (see rule 6).
- **No hook titles, slogans, rhetorical-question headers, or anthropomorphized model behavior** (see rule 7).
- **No out-of-scope content added for a nicer ending** (see rule 8).

---

## Working with the base pptx skill

1. Read `/mnt/skills/public/pptx/SKILL.md` for generation mechanics (pptxgenjs to build, LibreOffice+pdftoppm to render, the visual QA loop).
2. Apply this skill's rules 1–10 for every styling and wording decision.
3. For spotlight/progressive sequences (rules 4–5), generate the near-identical slides programmatically — build the diagram once as data, then emit one slide per reveal step, changing only opacity/color/highlight of the elements. This keeps positions pixel-identical so nothing jumps.
4. Run the base skill's **visual QA loop**, and additionally check: is exactly one thing spotlighted per reveal step? is the progress bar's current/faded state correct on each slide? did any faded element or light arrow become unreadable? are all brand icons real (not drawn/circled)?
5. Then reread every line of slide text and speaker notes for rules 6–8: any metaphor, slogan, hook title, rhetorical question, anthropomorphized model, line that only restates the figure, or content outside the requested scope? Remove or rewrite it.
6. If icons couldn't be fetched, list which ones and where you used neutral stand-ins.

See `references/checklist.md` for a quick pre-delivery checklist.
