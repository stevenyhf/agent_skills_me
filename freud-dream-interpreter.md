---
name: freud-dream-interpreter
description: Freud-based dream analysis using wish-fulfillment theory.
version: 0.1.0
metadata:
  hermes:
    tags: [Psychology, Dreams, Freud, Psychoanalysis]
---

# Freudian Dream Interpreter

Apply Sigmund Freud's dream theory (from *Die Traumdeutung*, 1900) to user-supplied dream content. Produces a structured interpretation that distinguishes manifest from latent content, identifies wish-fulfillment, and locates dream-censorship mechanisms. Pure knowledge skill — stdlib only, no external services.

This skill does NOT do: fortune-telling, mystical interpretation, Jungian archetypes, brain-science dream analysis, or clinical therapy. It operates strictly within Freud's published framework as recorded in the 12-volume *弗洛伊德大全集名著译著经典套装*.

## When to Use

- "我昨晚做了一个奇怪的梦..."
- "帮我分析这个梦"
- "解梦 / 释梦 / 弗洛伊德释梦"
- "这个梦代表什么?"
- "梦境分析 / dream interpretation"
- "我梦见 X,这是什么意思?"
- Any Chinese/English user describing dream content and requesting interpretation

## Prerequisites

- No external dependencies (pure methodology skill)
- No API keys / credentials
- No environment variables
- No scripts (all logic embedded in Procedure section)

## How to Run

Load this SKILL.md through `read_file`, then execute the 6-step Procedure below on the user's dream content. No shell commands required.

## Quick Reference

- Core distinction: `manifest content` vs `latent content`
- Core thesis: every dream is **wish-fulfillment**, even nightmares
- Four dream-work mechanisms: **condensation** + **displacement** + **representability** + **secondary revision**
- Method: **free association** — segment the dream, never interpret it whole
- Key concepts: censorship, disguise, composite image, symbolism, recent-trivia rule, childhood memory
- Reference dream: **Irma's Injection** (1895.7.23-24)

## Procedure

### Step 1: Receive and Segment the Manifest

When user describes a dream:
1. **Record verbatim** — do not fix logic, do not fill gaps
2. **Decompose into N elements**: people, places, objects, actions, dialogue, emotions
3. **Note user's reported emotional tone**: pleasant, anxious, angry, sad, fearful, calm, emotionless

**Never do**:
- Do not ask user to "tidy up" their description
- Do not complete "missing" plot points
- Do not modify user's original wording

### Step 2: Conduct Free Association

For each element, guide the user through free association. **Critical principle**: this is the soul of dream interpretation — the user must provide their own associations; the AI cannot substitute.

Use this prompt template (for each element):

```
"梦中出现 [element X],它让你联想到什么?
想到什么都可以,不需要合乎逻辑,
哪怕是无关的、不重要的、不好意思说的都请说出来。
弗洛伊德说过:席勒写信给朋友说,
阻碍创造力的是理性对涌入观念的过度审查。
我们要做的正是暂时关闭这种审查。"
```

**Follow-up prompts** (after user's first-layer association):
- "这个联想又让你想到什么?"
- "[association X]在你童年或最近有什么具体的事?"
- "你说 [association X],这种感觉(情绪)在你生活中什么时候还出现过?"
- "如果 [element X] 是一个人/动物/物体,谁/什么最像它?"

**Important**:
- User resistance ("我不确定"、"这很奇怪"、"没什么好说的") is itself important material — it indicates the element touches a **repressed wish**
- Don't rush; allow silence
- Never substitute associations for the user, even if you "know" the answer

### Step 3: Analyze Manifest-Latent Relationship

Based on user's free-association material, perform:

#### 3.1 Identify Condensation

Does one manifest element correspond to multiple latent thoughts?

**Criteria**:
- A dream person is a **composite image** — overlapping features of multiple real people
- A dream action represents multiple intentions
- A dream object simultaneously references multiple things

**Irma's dream example**: throat white spots = Irma's friend's diphtheria + Freud's eldest daughter's illness + Freud's own nasal cocaine damage

#### 3.2 Identify Displacement

Does the manifest's "important" element become "unimportant" in latent? Or vice versa?

**Criteria**:
- Manifest's "protagonist" is a minor person in latent
- Manifest's "background" small object carries core emotion in latent
- A number, color, or place is "overemphasized" in manifest — that's displacement's target

**Freud's principle**: "What stands out in the manifest is far from central in the latent; and vice versa."

#### 3.3 Identify Symbolism

Does the manifest use **cross-cultural stable symbols**?

**Common symbol table** (Freud-confirmed):

| Manifest element | Possible latent meaning |
|------------------|-------------------------|
| King/queen/leader | Father/mother |
| Child/son/daughter | Male sexual organ / repressed desire |
| House/room/door | Body (female); vagina (door, entrance) |
| Long hard objects (stick, knife, snake, cane, umbrella, tree) | Male genitals |
| Hollow objects (box, bottle, jar, room, cave, boat, ditch) | Female genitals |
| Climbing/up stairs/down | Sexual intercourse (rhythmic matching) |
| Falling/flying/swimming/floating | Sexual excitement; loss of control |
| Nakedness/exposure | Repressed childhood exhibition scene |
| Teeth falling out | Castration anxiety / loss of sexual potency |
| Death/funeral | Castration; post-orgasmic release; end of intimate relationship |
| Being chased/fleeing/cannot move | Moral censorship (repressed desire surfacing) |
| Exam/lateness/missing train | "Trial dream" — real childhood event replay |
| Water/flood/river | Birth / urination / intercourse |
| Food/feast/eating | Sexual acquisition |

**Warning**: symbols are not a fixed codebook; they must be combined with user's association context. Freud warned: "The key to symbolism must not be the interpreter's arbitrary choice."

#### 3.4 Identify Secondary Revision

Does the manifest have an overly "complete" plot or "coherent story"?

**Criteria**:
- The dream's logical coherence — if "too complete" or "too didactic", that's revision
- Manifest contains "moral lessons", "judgments", "self-justifying" endings
- The manifest "interprets itself" (someone in the dream tells the dreamer "this means...")

**Freud**: "Dream-work in its final stage rewrites the material into an almost coherent, comprehensible form — this is misleading because it masks the real unconscious process."

### Step 4: Infer the Latent Wish

Based on the analysis, **must** answer:

1. **What wish does this dream fulfill?** (wish-fulfillment)
2. **Is this wish repressed or acknowledged?**
3. **Why is this wish disguised/distorted?** (censorship)
4. **Is there a recent daytime event as trigger?**

**Critical principles** (Freud):
- **Even nightmares/anxiety-dreams** are wish-fulfillment — just deeper wishes
- Anxiety itself is not opposed to the wish; it's **censorship's reaction to almost-surfacing repressed wish**
- Children's dreams are often **un-disguised wish-fulfillment** (weaker censorship)
- Adult anxiety dreams often reflect **censorship failure** — repressed wish forces through

**Irma's dream template**:
- Manifest: Irma's illness, Otto's injection
- Latent 1: retaliation against Otto's "blame" (counter-accusation)
- Latent 2: self-defense — treatment failure is not my fault
- Latent 3: hint at Irma's widowhood (sexual repression)
- **Core wish**: absolution, exoneration, revenge on Otto

### Step 5: Output Structured Interpretation Report

Use this template:

```
【弗洛伊德释梦报告】

【显梦】你描述的梦境:
[User's original description, verbatim]

【显梦元素分解】
1. [Element 1]: [Association material summary]
2. [Element 2]: [Association material summary]
...

【释梦分析】
主导机制: condensation / displacement / symbolism / revision
集合形象 (if any): [Dream person X] may be composite of [Real person A] + [Real person B]
移置方向: [Manifest's important element] = [core/peripheral/irrelevant] in latent
象征解读: [Manifest element] hints at [physiological/emotional/memory]

【隐梦推断】
This dream fulfills the wish for: [specific description]
Trigger event: possibly [recent daytime event]
Repressed content: [Associations user resists speaking — marked "压抑区"]

【梦的伪装原因】
Why does this wish need disguise? Censorship motive:
- [Moral pressure] / [shame] / [self-protection]
- This disguise reflects: when awake, dreamer doesn't permit [specific behavior]

【弗洛伊德原典引证】
[Quote from Die Traumdeutung with chapter reference]

【给梦者的话】
- This analysis is possibility, not conclusion
- True dream interpretation requires the dreamer's own deep introspection
- If an association makes you resist, that's the most important clue
```

### Step 6: Quality Self-Check (Mandatory)

After completing the report, verify:

- [ ] Distinguishes manifest vs latent? **(required)**
- [ ] Identifies at least one condensation/displacement mechanism?
- [ ] Gives a specific "wish-fulfillment" inference (not vague "reflects anxiety")?
- [ ] Quotes Die Traumdeutung or its original meaning?
- [ ] Marks the **repression zone**?
- [ ] Avoids mysticism / fortune-telling / metaphysics?
- [ ] States clearly this is "possibility" not "conclusion"?
- [ ] Encourages user to continue self-exploration?

## Pitfalls

### 1. Don't treat "symbols" as a codebook

Freud explicitly rejected "decoding" dreams via fixed translation table: "The essence of decoding is not to interpret the dream as a whole, but to interpret its components individually… Obviously, this decoding dream-interpretation is a result of the dream's discontinuity and chaos."

**Correct**: symbols must be validated by user's free association.

### 2. Don't treat nightmares/anxiety-dreams as counter-wish-fulfillment

Anxiety dreams ARE wish-fulfillment — just deeper wishes. Freud: "Anxiety itself is not the force opposing the wish, but censorship's rebellion against the almost-surfacing repressed desire."

**Correct**: nightmares often reveal repressed wishes MORE clearly than pleasant dreams.

### 3. Don't substitute associations for the user

The **core step** of dream interpretation is the user's free association. If the AI directly "reads" dream elements, skipping this step, it abandons the soul of dream work — the fatal flaw of most pseudo-interpretation AI.

**Correct**: For every element, guide user to speak their associations. If user says "I can't think of anything", ask "What feeling does this give you?" — feelings are associations.

### 4. Don't ignore the "recent-trivia rule"

Freud found: **dream content is often a trivial daytime matter** (seeing a book, hearing a phrase, meeting a person), not an important event. This is displacement's trace — disguising important events as trivial images.

**Correct**: In Step 2, especially ask "the day before the dream, any trivial small thing happen?"

### 5. Don't give "definitive conclusions"

Dream interpretation is **possibility analysis**, not code-breaking. Freud: "I would not pretend I have uncovered this dream's full meaning, nor that my interpretation is impeccable."

**Correct**: Always use "possibly", "tends to", "reflects a possibility" — never "this IS…", "represents…".

### 6. Don't ignore children's dream special value

Children's dreams are often **un-disguised wish-fulfillment** — because children's censorship is weak, superego and ego not yet fully built. When analyzing adult dreams, ask "did you have similar dreams or experiences as a child?"

### 7. Don't mix other schools

Freudian dream work is completely different from Jung, Adler, neuroscience "REM activation". If user explicitly requests another school, switch to the corresponding skill.

### 8. Don't use as clinical diagnosis

Dream interpretation is a method for exploring the unconscious, **not psychotherapy**. If the user's dream reflects serious trauma, depression, suicidal thoughts, **recommend professional help**, not use this skill as substitute.

## Verification

After completing one interpretation, verify the report meets:

1. Manifest decomposition lists all elements
2. Each element has user's association material (not AI-substituted)
3. Clearly marks condensation/displacement/symbolism/revision mechanisms
4. Gives specific "wish-fulfillment" inference
5. Quotes Die Traumdeutung text
6. Marks "repression zone"
7. Uses uncertainty phrasings ("possibly", "tends to")
8. Ends encouraging continued self-exploration

**Pass standard**: all 8 met. If fewer than 5 met, interpretation depth insufficient.

## Theoretical Source

This skill is fully grounded in (from *弗洛伊德大全集名著译著经典套装*, 车文博主编, 2014):
- 《释梦(上)》(1900) — Chapters 1-6
- 《释梦(下)》(1900) — Chapter 7 and appendix
- 《论梦》(1901) — 13-section overview
- 《精神分析导论》 Lecture 11 "Dream" (1915-1917)
- 《释梦在精神分析中的运用》
- 《论释梦的理论与实践》

**Core quotes**:
- "梦是一种愿望的满足" (Chapter 3 title)
- "梦的显意与隐意" (Chapter 4)
- "梦的工作 = 凝缩 + 移置 + 表现力考虑 + 润饰" (Chapter 6)
- "梦的稽查作用" (Lecture 9)
- "梦是保护睡眠的反应" (Introductory Lectures 11)

## Reference Dream Examples (Analysis Templates)

### Template 1: Irma's Injection Dream (1895.7.23-24)

**Manifest**: Irma at party; Freud scolds her for refusing treatment. White spots in throat. Otto injects her with "propyl". Dr. M says "no matter".

**Latent**: Retaliate against Otto's blame; defend against treatment failure; hint at Irma's widowhood; trimethylamine = sex reference.

**Core wish**: **Absolution, exoneration, revenge on Otto**.

**Mechanisms**:
- **Condensation**: Irma = Irma herself + Irma's friend + female official + two former patients
- **Displacement**: Otto's blame (latent core) → transferred to Otto's injection error (manifest surface)
- **Symbolism**: throat white spots = sexual organ/disease (hint)
- **Revision**: whole dream forms a "defense" complete structure (multiple mutually exclusive excuses)

### Template 2: Botanical Monograph Dream

**Manifest**: Freud writes a monograph on primrose plants; book has dried specimens and color plates.

**Latent**: Conversation with ophthalmologist (Königstein) — cocaine, glaucoma, surgery, self-recommendation.

**Core wish**: **"I am the author of a valuable paper"** — self-praise.

**Mechanism**: **Displacement** — uses "botanical monograph" (trivial daytime impression) to substitute for "ophthalmologist conversation" (important event).

### Template 3: Mountain Climb Dream (5-year-3-month boy)

**Manifest**: Boy dreams of climbing to Dachstein mountain's Simony hut.

**Latent**: Was told during the day that Dachstein is behind, not under, the visible mountains — he was disappointed.

**Core wish**: **Un-disguised wish-fulfillment** — children's dreams barely disguise.

**Mechanism**: **Compensation** — daytime unfulfilled wish, directly realized in dream.

## Trigger Scenarios (for Hermes skill routing)

| User input example | Trigger? |
|-------------------|----------|
| "我昨晚梦见蛇,是什么意思?" | Yes |
| "帮我解梦,我梦见自己飞起来" | Yes |
| "用弗洛伊德的理论分析这个梦" | Yes |
| "dream interpretation for me" | Yes |
| "我做了个噩梦,很害怕" | Yes |
| "分析我儿子的梦(3 岁)" | Yes |
| "我梦见考试迟到" | Yes |
| "我梦见牙掉了" | Yes |
| "I dreamed about falling" | Yes |
| "梦境里我被追杀" | Yes |
| "为什么我总是梦见同一个地方?" | Yes (interpretable) |
| "我梦见去世的亲人" | Yes (cautious — may be grief response, not simple wish-fulfillment) |
| "梦境有什么科学解释?" | No (route to neuroscience skill) |
| "用荣格的方法解梦" | No (route elsewhere) |
| "我失眠多梦怎么办?" | No (clinical — recommend doctor) |
| "占卜我的未来" | No (unrelated) |