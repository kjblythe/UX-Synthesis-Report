# GLP-1 SUPPORT APP — USABILITY TESTING SYNTHESIS

## Master Reference Document

**Study:** In-person moderated usability testing, Bala Cynwyd PA, April 7 2026
**Participants:** 7 of 8 recruited (P08 no-show)
**Sessions:** 7 back-to-back, 2 rotating moderators (Allison, Jack)
**Observers:** Kyle, Allen, Lisa — rotated roles throughout the day. The observer framework had 3 fields: Rainbow Grid (structured behavioral tracking), and 2 freeform observer note slots. The person on Rainbow Grid duty could also pop quick observations into the freeform fields. Roles rotated so no single observer was locked into one method all day.
**Additional data:** Facilitator observation sheets, raw transcripts (7), Dovetail summaries + insights
**Target demographic (business):** Women aged 50-65. The recruited cohort skewed younger (mean ~48, range 36-61) but P05 (61F) and P07 (57F) are squarely in the target range, and P07 in particular validated the app’s accessibility for this audience.

**Study design note — features NOT shown:**

- The production app includes a **catch-up logging feature**: at the end of the day, the evening reflection includes an option to quickly log anything forgotten during the day (sacrificing detail for capture). The morning reflection includes a catch-up for the previous day’s unlogged items. This feature was not included in the prototype, so participant feedback about wanting to log meals later (e.g., P07’s business lunch concern) is already addressed in the production design.

-----

## PHASE 1: QUANTITATIVE & STRUCTURED DATA SPINE

### 1. Participant Demographics

|ID |Age|Gender|Medication                     |Duration|Nutritional Default|Prior Apps                        |App Comfort (1-7)|Tries New vs. Same|
|---|---|------|-------------------------------|--------|-------------------|----------------------------------|-----------------|------------------|
|P01|36 |F     |Wegovy                         |5 months|Calorie            |MyFitnessPal, Apple Health        |7                |Same              |
|P02|44 |M     |Wegovy / Factor VIII           |5 months|Macro              |MyChart, Microhealth, Apple Health|7                |Same              |
|P03|54 |F     |Wegovy                         |6 months|Calorie            |WeightWatchers, Healthi           |6                |Tries new         |
|P04|49 |F     |Zepbound                       |4 months|Macro              |MyFitnessPal, Apple Health        |6                |Same              |
|P05|61 |F     |Zepbound + methotrexate, Enbrel|1 year  |Calorie            |Shotzy                            |7                |Tries new         |
|P06|36 |F     |Zepbound                       |2 months|Macro              |Apple Health, Dexcom              |6.5              |Tries new         |
|P07|57 |F     |Zepbound                       |5 months|Calorie            |Apple Health                      |5                |Tries new         |

**Summary:** Mean app comfort 6.4/7 (range 5-7). 6/7 female, 1 male. Age range 36-61 (mean ~48). All iPhone users. All right-handed except P05 and P07 (left). Nutritional display alternated calorie/macro across sessions. All had prior health app experience per screening criteria.

**Notable context:**

- P01: First session of the day (9am). Low energy throughout — possibly tired/hungover. Vehemently opposed to reflections.
- P02: Only male participant. Uses Microhealth for IV infusion tracking — noted his current app doesn’t support GLP-1 logging.
- P03: Consistent low scorer across the board (mean post-session 5.8/7 vs. group mean 6.6). Most critical participant.
- P05: Oldest participant (61). Recognition-vs-recall failure on Learn tab — found it during exploration but couldn’t relocate during directed task.
- P07: Lowest self-reported tech comfort (5/7) but paradoxically grasped navigation most intuitively of all participants.

-----

### 2. SEQ Scores by Task

|Task              |P01|P02|P03|P04|P05|P06|P07|Mean               |vs. Benchmark (5.3-5.6)|
|------------------|---|---|---|---|---|---|---|-------------------|-----------------------|
|T1: Home Screen   |7  |7  |6  |7  |7  |6  |7  |**6.7**            |Above                  |
|T2: Log Medication|7  |7  |4  |7  |7  |7  |7  |**6.6**            |Above                  |
|T3: Log a Meal    |7  |7  |5  |7  |7  |7  |7  |**6.7**            |Above                  |
|T4: AI Chat       |5  |7  |4  |5  |6  |6  |5  |**5.4**            |At benchmark           |
|T5: Learning      |7  |7  |7  |5  |4  |7  |7  |**6.3**            |Above                  |
|T6: Reflection    |*  |7  |7  |7  |6  |7  |7  |**6.9** (excl. P01)|Well above             |

**T6 P01 note:** SEQ discrepancy between sources. Facilitator recorded 7 (ease of finding it — she found it immediately). Rainbow grid recorded 1 (she refused to engage with reflections). Resolution: the feature was **discoverable but rejected** by P01. She saw it immediately but was vehemently opposed to the concept. This is not a usability failure — it’s a preference/attitude finding. For scoring purposes, the task was a Fail on completion but the UI itself scored 7 for discoverability ease.

**Key signal:** T4 (AI Chat) is the only task at benchmark rather than above it. Three participants (P01, P03, P07) scored ≤5. This is the primary usability gap. **⚠️ Note: PL1 (inconsistent chat logging) and PL4 (variable AI responses) may contribute to the lower scores. The discoverability problem is real, but some task friction may be prototype-specific.**

**P03 pattern:** Lowest scores on T2 (4), T3 (5), T4 (4). Most critical participant overall but still rated the app positively in post-session.

-----

### 3. Task Completion

|Task              |Full|Partial|Fail|Key Notes                                                                                                    |
|------------------|----|-------|----|-------------------------------------------------------------------------------------------------------------|
|T1: Home Screen   |N/A |N/A    |N/A |Exploratory — no pass/fail criteria                                                                          |
|T2: Log Medication|7/7 |0      |0   |100% success. 3/7 initially went to meds screen first (P03, P05, P07)                                        |
|T3: Log a Meal    |7/7 |0      |0   |100% success. P03 had backtracking issue (Panera source). P04 had trouble with card + button                 |
|T4: AI Chat       |4/7 |3      |0   |P03 partial (limited engagement), P04 partial (didn’t independently find coach), P06 partial                 |
|T5: Learning      |5/7 |1      |1   |P04 partial (navigation confusion within Learn), P05 fail (didn’t find Learn independently)                  |
|T6: Reflection    |4/7 |2      |1   |P01 fail (refused to engage), P02 partial (used AI Coach instead), P03 partial (entered “yes” for everything)|

-----

### 4. Navigation Patterns

#### T1 — Home Screen First Impressions

- **Noticed wellness score:** P01, P03, P06, P07 (4/7 per facilitator data; rainbow grid shows 6/7 — discrepancy may be due to different thresholds for “noticed”)
- **Scrolled below fold:** 7/7
- **Spotted + button:** P01, P06 only (2/7) — **CRITICAL FINDING**
- **Noticed tab bar:** P01, P02, P04, P05 (4/7 per rainbow grid)
- **Noticed insight/reflection cards:** P01, P02, P04, P05, P06, P07 (6/7)
- **Can articulate app purpose:** 7/7 — all could describe the app’s purpose accurately

#### T2 — Medication Logging Entry Point

- **+ button:** P01 only (1/7)
- **Home card / tab bar:** P02, P03, P04, P05, P06, P07 (6/7)
- **Initially went to meds screen (error recovery):** P03, P05, P07 (3/7) — they expected to log medication from the medication section of the wellness score or the meds icon. P07’s observer note: the syringe icon on the medicine section made her think injection logging would be there.
- **Found body map injection site:** 7/7 (100%)
- **Body map usefulness rating:** Mean 6.7/7 — universally valued

#### T3 — Meal Input Method

- **Photographed image:** P02, P03, P04, P05, P06, P07 (6/7) — **dominant pattern**
- **Typed/described:** P01 (1/7) — typed ingredients in detail, chose “describe” option
- **Manual entry:** 0/7
- **Entry path — Nutrition tab:** P02 (via card), P03, P04, P05, P07 (via card)
- **Entry path — + button from Home:** P01, P06 (2/7)
- **Felt nutritional info accurate:** 7/7
- **Nutritional detail level:** 2/7 wanted more detail (P04 wanted quantities, P06 wanted more specific info), 5/7 said about right

#### T4 — AI Coach Discovery (Part A, unprompted)

- **Found AI Coach independently:** P02, P03 (2/7 per facilitator data) — possibly P06 as well (facilitator shows she found it but rainbow grid is ambiguous)
- **Went to Progress first:** P01, P05, P07 (3/7)
- **Went to Wellness Score / Home insights:** P04, P05 (2/7)
- **Needed guided bridge:** P01, P04, P05, P07 (4/7) — majority needed guidance
- **Types natural conversational query:** 7/7 once in the chat — no one struggled with the interaction model itself
- **Preferred UI over chat for logging (after reveal):** P01, P02, P03, P05, P06, P07 (6/7)
- **Preferred chat over UI:** P04 (1/7)
- **Sees AI as useful (not novelty):** 7/7

**Key insight:** The discoverability problem is finding the AI Coach, not using it. Once there, everyone engaged naturally and found it valuable. 6/7 still preferred UI screens for logging tasks, but saw AI as complementary for questions, summaries, and recipes.

#### T5 — Learning Pathways

- **Found Learn directly:** P01 (after detour), P02, P03, P06, P07 (5/7 found it independently per facilitator)
- **Did not find independently:** P04, P05 (2/7)
- **Understands pathway structure:** 7/7
- **Engages with lesson content:** 7/7 (once found)
- **Positive reaction to format:** P02, P03, P05, P06, P07 (5/7) — but P06 notably called it “Chutes and Ladders” (negative)
- **Went deeper in lessons:** P04, P06, P07 (3/7)

**P05 anomaly:** Found Learn during initial exploration (T1) but could not relocate it during directed task (T5). Classic recognition-vs-recall failure. Supports the bottom nav invisibility pattern.

#### T6 — Evening Reflection

- **Found evening card on home screen:** P03, P04, P05, P06, P07 (5/7)
- **Went elsewhere first:** P01 (progress → couldn’t find it), P02 (AI Coach — asked it to journal)
- **Engaged thoughtfully:** P04, P05, P06, P07 (4/7)
- **Rushed/minimal engagement:** P03 (entered “yes” for everything)
- **Refused to engage:** P01
- **Connects reflections to learning:** P03, P04 (2/7 explicitly)
- **Comments on time-of-day change:** P04, P07 (2/7)

-----

### 5. Post-Session Questionnaire (1-7 Likert)

|Item                          |P01    |P02    |P03    |P04    |P05    |P06    |P07    |Mean   |
|------------------------------|-------|-------|-------|-------|-------|-------|-------|-------|
|Has features I’m looking for  |7      |7      |5      |7      |7      |6      |7      |**6.6**|
|Easy to use                   |7      |7      |6      |7      |7      |6      |7      |**6.7**|
|Trust with health info        |7      |7      |7      |7      |7      |6      |5      |**6.6**|
|Daily routine fit             |7      |7      |6      |7      |7      |6      |7      |**6.7**|
|AI feels helpful, not gimmicky|7      |7      |6      |7      |6      |7      |6      |**6.6**|
|Understands my journey        |7      |7      |5      |7      |6      |6      |7      |**6.4**|
|**Participant Mean**          |**7.0**|**7.0**|**5.8**|**7.0**|**6.7**|**6.2**|**6.5**|**6.6**|

**Overall mean: 6.6/7.** Extremely positive. P03 is the consistent low scorer (5.8 mean). P01, P02, P04 gave straight 7s.

-----

### 6. Nutritional Display Preference

|Metric                    |Count|Participants                        |
|--------------------------|-----|------------------------------------|
|Preferred calorie view    |6/7  |P01, P02, P03, P04, P06, P07        |
|Preferred macro/guide view|1/7  |P05 (protein is her priority macro) |
|Would switch between views|1/7  |P06 (wanted info from both combined)|
|Would stick with one view |5/7  |P02, P03, P04, P05, P07             |
|Values having the toggle  |3/7  |P01, P05, P06                       |

**Key finding:** Calorie view is the clear default preference regardless of which view participants were initially shown. Even P02 (started on macro) preferred calorie. The macro/guide view needs either a redesign or repositioning as an opt-in secondary view.

-----

### 7. End-of-Day Team Synthesis (captured day-of)

#### Top 5 Usability Issues (team consensus)

1. Almost everyone expected to log injections from the meds panel. People thought they could change dosages there.
1. Nobody used the + button — needs restyling. Few people noticed the bottom navigation at all.
1. People had a lot of trouble finding/viewing “progress”
1. People did not think to go to AI Chat to check on status
1. The chat logger didn’t show previous injection sites. Need to link to the full card for complex interactions.

#### Top 3 Things That Worked Well

1. Injection flow and body map (universally loved)
1. Meal logging with AI photo (big win)
1. AI Coach, once people started using it

#### Participant Suggestions (captured day-of)

1. Favorite a logged meal so you can re-log it quickly
1. Add backdating for meal logging
1. Barcode scanning for packaged food
1. Progress as a calendar with arrows
1. Video (NotebookLM-generated) for every article

-----

### 8. Key Quotes Index

Quotes captured from observer notes and facilitator data. Will be supplemented/verified with transcript timestamps in Phase 2.

|ID |Task|Quote / Paraphrase                                                                                                                        |Source          |Context                                 |
|---|----|------------------------------------------------------------------------------------------------------------------------------------------|----------------|----------------------------------------|
|P01|T1  |“Everything is categorized, I like that”                                                                                                  |Observer (Allen)|Exploring home screen                   |
|P01|T2  |“It’s a pretty cool app honestly”                                                                                                         |Observer (Lisa) |After logging medication                |
|P01|T6  |“It’s nice but to me typing that in is not rewarding for me”                                                                              |Observer (Allen)|Refusing to engage with reflections     |
|P02|T2  |“This is a lot better than what I use now”                                                                                                |Observer (Lisa) |Comparing to Microhealth                |
|P02|T2  |“Shows your recent [injection site], that’s pretty cool”                                                                                  |Observer (Lisa) |Reacting to body map                    |
|P02|T4  |“I expected things like that in Coach, but didn’t know you could also log an injection there”                                             |Observer (Allen)|After reveal                            |
|P03|T2  |“It was easier because you had the card right there”                                                                                      |Observer (Allen)|After finding injection logging via card|
|P03|T3  |“I would like if standard serving sizes were suggested”                                                                                   |Observer (Allen)|Nutritional display feedback            |
|P03|T5  |“Great information that you don’t always get”                                                                                             |Observer (Allen)|Reacting to learning content            |
|P03|T6  |“Natural to ask the questions. Not sure if I would have the answers”                                                                      |Observer (Allen)|On reflection prompts                   |
|P04|T4  |“[She] did not know what the coach was”                                                                                                   |Facilitator data|Failed to find AI Coach independently   |
|P04|T4  |“Would like ideas for gentler food [because she] gets nausea”                                                                             |Facilitator data|Meal planning feedback                  |
|P05|T4  |[Typed] “How am I doing?”                                                                                                                 |Facilitator data|Natural query phrasing in AI Coach      |
|P05|T4  |“Would think of [the AI Coach] as a buddy on her weight loss journey”                                                                     |Facilitator data|AI perception                           |
|P06|T5  |“Feels like Chutes and Ladders”                                                                                                           |Facilitator data|Learning pathways format criticism      |
|P06|T5  |“Why does it have squiggles instead of bullets?”                                                                                          |Facilitator data|Learning pathways format confusion      |
|P06|T4  |“It was cool to get personalized feedback”                                                                                                |Facilitator data|AI Coach reaction                       |
|P06|T1  |“[The app] seems to combine the features of more than one app”                                                                            |Facilitator data|Home screen first impression            |
|P07|T4  |[Typed] “How many calories do I have left?”                                                                                               |Facilitator data|Natural query phrasing in AI Coach      |
|P07|T6  |Would be more likely to use reflections “if the system prompted her”                                                                      |Facilitator data|Reflection engagement condition         |
|P07|T4  |“It was really easy. Liked that it was focused on the app and what she is going through”                                                  |Facilitator data|AI Coach reaction                       |
|P07|Post|“It would be great if the advertising could be geared towards tracking your weight loss journey. Weight loss is more than taking medicine”|Facilitator data|Final debrief                           |

-----

### 9. Emerging Findings (Pre-Transcript, Subject to Verification)

These are the patterns emerging from the structured data. They will be confirmed, nuanced, or revised during Phase 2 transcript analysis.

#### HIGH-PRIORITY FINDINGS

**F1: Interactive elements lack visual differentiation from the surrounding UI.** The app’s visual cohesion — which participants praised — comes at the cost of affordance clarity. This manifests across multiple surfaces: only 2/7 spotted the + button; 4/7 noticed the tab bar; the evening reflection card was missed by 2/7; toast notifications for completion states went unnoticed (participants couldn’t tell when actions like meal logging were actually confirmed); and the meal logging card’s decorative icon was mistaken for the tappable button (F11). These are not isolated issues — they share a root cause. Functional/interactive elements (bottom nav, + button, toast notifications, card CTAs) are styled too similarly to informational/decorative elements. The app needs a clearer visual language that distinguishes “things you tap” from “things you read.”

**F1a: Toast notifications are not functioning as completion confirmation.** Dovetail’s cross-session analysis confirmed that participants were not picking up on toast notifications as reliable confirmation signals. Instead, they relied on three alternative cues: (1) the home screen card disappearing after logging (P02: “it went away on the home screen, so I’m pretty sure I did log it”; P07: “the actual box went away after I logged it, visually telling me you’ve logged that”; P03: “I noticed that once you do that, that goes away”), (2) the in-flow confirmation/review screen (P01: “I got the confirmation”), or (3) remained uncertain (P04: “I did not know it was done until I knew it was done”; P06: “I kind of wish under injection day it would say ‘last logged’”). **Design recommendation: add persistent state indicators on the home screen (e.g., “last logged: today”) and ensure structural UI changes (card removal, state update) serve as the primary completion signal, not transient toasts.**

**F2: AI Coach is valuable but undiscoverable.** Only 2-3/7 found it independently when given a summary/progress task. Once guided there, 7/7 engaged naturally, typed conversational queries, and found it useful. 7/7 said it was useful (not novelty). But 6/7 still preferred UI screens for logging tasks. The AI Coach’s value is as a complementary intelligence layer (questions, summaries, recipes, feedback), not as a replacement for direct UI interactions. **⚠️ Note: The 6/7 UI-over-chat preference for logging may be partially inflated by PL1 (chat logging was inconsistent in the prototype). In at least one case (P02), the chat explicitly redirected the user to the + button rather than logging inline. The true preference split in a production build with reliable chat logging may differ.**

**F3: Photo-based meal logging is a breakout feature.** 6/7 chose to photograph the image unprompted. Multiple participants expressed surprise and delight. P04: “Would get lazy if required to type in each ingredient.” This is a key differentiator vs. competitors like MyFitnessPal.

**F4: Injection body map is universally loved.** 7/7 found it, 7/7 rated it highly (mean 6.7/7 usefulness). Multiple participants called it out as better than their current tools. P02: “This is a lot better than what I use now.”

#### MEDIUM-PRIORITY FINDINGS

**F5: Calorie view is the overwhelming preference.** 6/7 preferred it regardless of starting condition. Macro/guide view may need repositioning or redesign. Consider making calorie the default with macro as opt-in.

**F6: Meds screen expectation mismatch.** 3/7 initially tried to log injections from the medication section of the wellness score or meds icon. They expected logging functionality where they saw medication information. The syringe icon reinforced this expectation.

**F7: Learning pathways work but aren’t magnetic.** 7/7 understood the structure, 7/7 engaged with content. But enthusiasm was moderate — “would read once,” “if bored,” “toss-up between this and asking the chatbot.” P06’s “Chutes and Ladders” comment reflects unfamiliarity with Duolingo-style learning paths, not a design flaw — the pathway format supports branching and embedded reflections that require this structure. P02 praised the same format for the reasons it exists. The content is valued as a reference resource, particularly for newer users; the format may benefit from a brief onboarding cue explaining the pathway metaphor, but should not be flattened to a list.

**F8: Reflections are polarizing.** 4/7 engaged thoughtfully, 1/7 rushed, 1/7 used AI Coach instead, 1/7 refused entirely. When engaged, participants found them meaningful. But willingness to do them daily is split. P07’s insight — “if the system prompted her” — suggests push notifications may be the key driver of adoption.

#### LOWER-PRIORITY / FUTURE CONSIDERATIONS

**F9: Users need temporal navigation for progress — daily, weekly, and date-specific views.** 3/7 participants independently sought a fast, non-AI path to “how am I doing?” — P01 expected a calendar icon, P03 wanted a homepage button (“it’s quicker, you don’t have to type a question”), P04 assumed the wellness score would show weekly status. The current progress icon (small up-trend on homepage) is not intuitive. The deeper design question this surfaces: should users be able to toggle between daily, 7-day, and 30-day summary trends? Should there be a calendar view that lets you go back and review everything that happened on a specific date? Both seem necessary — the first for trend awareness, the second for the “what did I eat last Tuesday?” use case that supports doctor visits (P01: “even if the doctor asks, ‘oh what day?’”) and pattern recognition (P04: “you can figure out why you emotionally ate”). The prominence and placement of this temporal navigation in the UI is a key design decision for the pilot build.

**F10: Dose customization expected.** P01 and P04 both tried to change the medication dose during logging. **⚠️ PL3: Feature not functional in prototype due to fixed persona data. Production app will tie to prescription.**

**F11: Card icon/button affordance confusion.** On the meal logging card, a decorative icon above the fold was mistaken for the tappable button, while the actual button sat below the fold. P04 hit this directly. This is a real UI issue — not a prototype limitation. The icon needs to either be made tappable or visually distinguished from the button, and the actual CTA needs to be above the fold.

**F11: Meal favoriting / re-logging requested.** P03 specifically requested ability to save standard meals for quick re-logging. Multiple participants mentioned this would make daily tracking more sustainable.

**F12: Voice input expected.** P05 and P07 both tried the microphone icon in AI Coach. P07 said she’d prefer voice for AI interaction. **⚠️ PL2: Mic was present in UI but non-functional in prototype. The attempts confirm real demand for voice input — this is a valid user need surfaced by the prototype, not a design gap.**

-----

## PHASE 2: PARTICIPANT-LEVEL TRANSCRIPT SUMMARIES

### P02 — Male, 44, Wegovy (5 months), Macro default

**Session duration:** 55:56 | **Moderator:** Allison | **Overall tone:** Engaged, positive, methodical

#### Warm-Up Context (00:00–07:38)

- App comfort: 7/7. Uses same apps consistently (not an explorer).
- Current tools: MyChart (appointments, bloodwork), Micro Health (weekly IV infusion logging — Factor VIII for bleeding disorder), Apple Health (step counting).
- Key motivation for Micro Health: “Sometimes I forget when I infuse, even though it’s only once a week. So I like to log it in, even have to go back for a doctor’s visit, just show them.” [03:12–04:55]
- Also tracks steps via Apple Activity; aims for 2,500+/day due to severe arthritis in knees. “I mostly lead a sedentary life because I have severe arthritis.” [04:00]
- Tried to add GLP-1 to Micro Health but couldn’t — this was an immediate pain point that made him interested in the prototype. [08:00]

#### T1: Home Screen Exploration (07:39–11:58) | SEQ: 7

- **First thing noticed:** Check-in feature and injection day reminder. [07:39]
- Immediately connected to his existing Micro Health gap: “The app that I use, I tried to add my GLP-1 to that, but I couldn’t. So I’m interested in this app.” [08:00]
- **Injection site rotation reminder** was the standout: “Sometimes I tend to forget, like when I put my GLP-1… I think I did the repetitive side like 2 weeks in a row and I don’t think you’re supposed to.” [08:30]
- Also noticed: headache check-in (“I do get a headache”), water intake tracking, meal logging.
- Could articulate app purpose: “Logging in your injection, tracking your meal intake, tracking your water intake, your activity, your meds, your mood.” [10:22]
- **Did NOT notice the + button or tab bar** during exploration.
- Nothing unclear. Positive surprise: injection site rotation reminder.

#### T2: Log Medication (11:59–16:16) | SEQ: 7

- **Entry path:** Used the home card carousel (“Login injection. It was right here… next to hydration.”) [13:57]
- Card label was clear enough that he went straight to it.
- **Delighted by body map:** “Oh, it’s interesting. Okay, let’s see what it does. It tells you your recent [injection site] was right there, and that’s pretty cool.” [12:25]
- “I like that you could backtrack an earlier injection.” [13:00]
- **Confirmation confidence: 7.** “It went away on the home screen. So I’m pretty sure that lets me know that I did log it in.” [14:28]
- Body map usefulness: 7. “I didn’t expect to have like prior injection sites… which is good.” [15:19]
- **Comparison to current tools:** “This is a lot better because the app that I use, I think it only tracks my infusions for my bleeding disorder.” [15:46]
- Would prefer to keep GLP-1 and infusion apps separate — the specialization is a feature, not a bug. [16:23]

#### T3: Log a Meal (17:03–25:51) | SEQ: 7

- **Input method: Photographed the image.** Went straight to “take a photo” option without noticing other choices. “No, I went straight to the photo.” [20:25]
- Did NOT expect AI photo recognition: “I thought I was gonna like search, have to search like the chicken and the tomatoes and the shaved carrots.” [19:30] — **strong positive surprise moment.**
- “I didn’t think it was gonna pick up the whole meal the way it did, so that was pretty cool.” [20:38]
- Liked the portion selection feature: “Sometimes, you know, you don’t want to eat the whole thing.” [18:07]
- **Nutritional accuracy:** Felt accurate. Green checkmark (“solid choice”) was the trust signal. [21:25–21:36]
- **Nutritional detail level:** “This kind of info I want… let you know you’re getting your protein.” Satisfied with current level. [22:01]
- **Display preference:** Preferred calorie view because it has pictures and calories. Does not currently count macros. [23:17–23:45]
- **Toggle:** “It wouldn’t matter. I mean, you have options, which is good, but either way I use one of them.” Would use whatever the default is. [24:45]
- **Daily tracking willingness:** “It’s fine. Most everybody has a cell phone in their hand anyway when they’re eating most of the time.” [25:16]

#### T4: AI Chat (25:51–35:15) | SEQ: 7

- **Part A — Found AI Coach independently.** “I guess I will go to Coach.” [26:55] — phrased tentatively but navigated directly.
- Used pre-populated “Check my progress” prompt. Read the summary aloud: “You’re off to a strong start. You’ve already lost 3 pounds and are maintaining a 7-day logging streak.” [27:25]
- **Unprompted exploration:** Typed “where was my last injection” — got injection site info. Realized he meant to ask “when” but the AI still answered usefully. Self-corrected and tried a refined query. [28:27–29:29]
- **Initial perception of AI Coach:** “At first I thought it was like a customer service type thing.” [31:49] — important mental model insight.
- **Why it’s useful:** “All that food intake, all that stuff, you know, remembering, remembers recipes, you know, things like that is just useful.” [32:00]
- **Reveal — logging via chat:** The AI Coach directed him back to the + button to log, rather than logging inline. “So I thought you was able to log it through the coach. It just tells you to go back to the main screen and hit the plus sign.” [34:35] — **⚠️ PL1: Prototype limitation. Chat logging was inconsistent in the Lovable build. Not a design decision.**
- **Chat vs. UI preference:** Prefers UI. “The plus sign is right there. It’s just a lot easier. The AI is good for other things.” [35:03]
- **Key quote that encapsulates the mental model:** The AI Coach is for questions, summaries, and guidance — not for logging. The UI is for action.

#### T5: Learning Pathways (35:26–41:44) | SEQ: 7

- **Found Learn directly** via tab bar. [35:50]
- Initial reaction: “It looks like it’s more like a coaching type thing, like supporting your metabolism, getting started. I don’t think I see anything about learning.” [36:15] — perceived as coaching, not learning.
- Needed prompt to click into content. Once inside: “I like how it is, because it starts from, you know, what is GLP-1, how does it work.” [37:21]
- **Pathway format:** Positive. “When you bunch a list together, kind of like scrambles your brain a little bit. It looks like too much to read, but this one separates it so it’s like individualized.” [38:13] — **strong endorsement of the pathway structure over lists.**
- **Would use:** “Especially if I’m new to GLP-1, I would like to know like what exactly is GLP-1, how does it work?” [41:12] — but acknowledged the content is most relevant for newer users.

#### T6: Evening Reflection (41:44–50:28) | SEQ: 7

- **Did NOT find the evening reflection prompt.** First went to Activity (steps, calories, active minutes). [42:30]
- When prompted about journaling: “You could do that? Like a journal? I’m missing—.” [42:58] — genuinely didn’t know the feature existed.
- **Recovery:** Asked the AI Coach for “journal” and got mood-logging prompts. Used pre-populated options but noted: “I don’t see where you could put personalized options.” [44:38]
- Facilitator eventually guided him to the reflect card on the home screen. He had not noticed it. “Maybe it’s the way it looks all together.” [45:35] — **bottom nav/card visibility issue confirmed.**
- Once engaged: positive. “It’s good, you know, whether you’re having a bad day or a good day, maybe you want to like, if you don’t want to talk to anybody, maybe you could just write about it.” [45:56]
- **Daily use:** Yes. “It’s like a journal, you want to, if not talk to somebody, basically talk to yourself or jot it down.” [47:40]
- **Learning-reflection connection:** “It kind of is… more so like a manual.” [48:52–49:03] — sees Learn as reference material, journal as personal expression.
- **Persona change:** Did NOT notice the time-of-day visual shift. “I didn’t notice, but I think it’s pretty cool.” [49:45] — thought sleep category should disappear in morning mode. [50:18]

#### Post-Session & Debrief (51:06–55:47)

- **How he’d describe it:** “Helps you track not only your injections but your injection site. Helps you with meal prep and logging in meals.” [53:17]
- **Most engaged moment:** Injection site reminder. [53:46]
- **Not frustrated** at any point. [53:46]
- **Comparison to current tools:** “There’s a lot more.” [54:16]
- **Genuinely useful feature not seen elsewhere:** “Reminder of the injection site, like last week’s injection. Mine doesn’t have that.” [54:32]
- **Daily routine fit:** Would use it. Primary use would be meal tracking, with GLP-1 tracking as secondary. [54:54]
- **Most valuable feature (questionnaire):** The injection reminder.
- **Would change:** Nothing. “Liked that it is for GLP-1.” [from facilitator data]

#### P02 Key Quotes for Report (with timestamps)

|Timestamp|Quote                                                                                                                 |Context                               |
|---------|----------------------------------------------------------------------------------------------------------------------|--------------------------------------|
|08:00    |“The app that I use, I tried to add my GLP-1 to that, but I couldn’t. So I’m interested in this app.”                 |Immediate identification of unmet need|
|08:30    |“Sometimes I tend to forget… I think I did the repetitive side like 2 weeks in a row”                                 |Injection site rotation pain point    |
|12:25    |“It tells you your recent [site] was right there, and that’s pretty cool”                                             |Body map delight                      |
|15:46    |“This is a lot better because the app that I use, I think it only tracks my infusions”                                |Direct competitor comparison          |
|19:30    |“I thought I was gonna have to search like the chicken and the tomatoes”                                              |Photo recognition surprise            |
|20:38    |“I didn’t think it was gonna pick up the whole meal the way it did, so that was pretty cool”                          |AI meal logging delight               |
|25:16    |“Most everybody has a cell phone in their hand anyway when they’re eating”                                            |Daily tracking acceptance             |
|31:49    |“At first I thought it was like a customer service type thing”                                                        |AI Coach mental model                 |
|34:35    |“I thought you was able to log it through the coach. It just tells you to go back and hit the plus sign”              |Chat logging limitation               |
|35:03    |“The plus sign is right there. It’s just a lot easier. The AI is good for other things”                               |UI vs. chat preference                |
|38:13    |“When you bunch a list together, kind of like scrambles your brain… this one separates it so it’s like individualized”|Learning pathway format endorsement   |
|42:58    |“You could do that? Like a journal? I’m missing—”                                                                     |Reflection discoverability failure    |
|45:35    |“Maybe it’s the way it looks all together”                                                                            |Why he missed the reflection card     |
|45:56    |“If you don’t want to talk to anybody, maybe you could just write about it”                                           |Reflection value proposition          |

-----

*P04 summary pending — awaiting transcript upload.*

-----

### P04 — Female, 49, Zepbound (4 months), Macro default

**Session duration:** 52:00 | **Moderator:** Allison | **Overall tone:** Engaged, practical, warm — the strongest overall advocate for the app

#### Warm-Up Context (00:00–05:57)

- App comfort: 6/7. Uses same apps consistently.
- Current tools: MyFitnessPal (stopped ~5 years ago when they started charging), Apple Health (step counting only — “not really to track food intake”).
- Key MFP feature she missed: barcode scanning. “I could scan a barcode and get information. It was easier to do that.” [03:37]
- Self-described as “lazy about logging food” — a strong signal about what input methods will work for her. [17:20]
- No current nutrition app — this is an unserved user.

#### T1: Home Screen Exploration (05:57–10:22) | SEQ: 7

- **First thing noticed:** Injection day reminder. “Actually, it’s a good reminder.” [06:12]
- Also noticed: sleep/steps tracking, colors (“I actually like the colors”), ability to track nutrition, mood, meds.
- Could articulate app purpose: “Keeping track of my daily activities, my nutrition, so basically my wellness.” [08:16]
- **Did NOT notice + button** during exploration.
- **Unclear element: AI Coach.** “The coach — is it a tutorial? Is it a more descriptive part of the app? Is it something giving you pep? Pumping you up?” [09:44–10:03] — **This is the clearest articulation of the Coach labeling confusion across all participants.**
- Nothing surprising: “They all look pretty normal.” [10:16]

#### T2: Log Medication (10:27–13:47) | SEQ: 7

- **Entry path:** Used home card (“Injection day” prompt). “You can click on injection day and then hit log injection.” [10:45]
- Smooth flow. Attempted to change dose but accepted the pre-populated value. [11:08] **⚠️ PL3**
- **Confirmation confidence: 7.** “It said confirm, and I just believed it.” [12:13]
- Body map usefulness: 6/7. “I didn’t think it would have where I injected.” [12:56] — positive surprise, slightly lower rating than other participants.
- **Comparison:** “I don’t typically log it, I just remember. So it’s actually a really good thing for someone who can forget sometimes.” [13:21]

#### T3: Log a Meal (13:47–20:56) | SEQ: 7

- **Entry path:** Went to Nutrition tab. Hit the decorative icon first (“Oh, I hit the wrong thing here”), then found the actual button. **This is the F11 card icon/button affordance finding.** [14:03]
- **Input method: Photographed the image.** “I’d love to do the take a photo.” [14:24] — expressed desire before even selecting it.
- **Confirmation gap:** “It was a 7, but I did not know it was done until I knew it was done.” [15:22] — she wasn’t sure the meal was fully logged after submitting. “I thought I had to log it, like confirm that it was logged.” [15:49] — **valid finding: meal logging completion state is unclear.**
- Why photo: “It was the easiest one… I will admit to being lazy for logging food. Like, putting it in every single piece of it takes so long that it’s not— it turns me off to have to do that.” [17:20] — **strongest quote on photo vs. manual effort.**
- **Nutritional accuracy:** Yes, but wanted more detail. “It’s too little. Like, I would want to see what exactly it said, like one whole chicken breast or half an avocado. How many tomatoes?” [18:50]
- **Display preference:** Started on macro, shown calorie — **preferred calorie view.** “Oh, I like that much better. It tells you how many carbs, how many grams of protein, it tells you all the details that you need to know.” [19:37–19:40]
- **Toggle:** Would pick one and stick. [20:10]
- **Daily tracking:** “If I could take a picture of it, I would do it all the time.” But manual: “It would be a pain in the butt… I know myself, I know I’d get lazy with it.” [20:23–20:33] — **Photo is the make-or-break for daily adoption for this user.**

#### T4: AI Chat (20:56–29:42) | SEQ: 5

- **Part A — Did NOT find AI Coach.** Went to Nutrition first (7-day calories, protein), then considered “the earned maybe?” [22:10], then settled on wellness score. “I would assume it’s in that wellness score… I’m assuming that would keep track of how well you’re doing on a daily basis.” [22:35–22:46]
- When asked why Coach didn’t come to mind: **“I just didn’t think about that. I wasn’t sure what the coach was.”** [23:25] — directly connects back to her T1 confusion about what “Coach” means.
- **Needed guided bridge** to AI Coach.
- **Once in Coach:** Immediately engaged. Used “Check my progress” prompt, then typed her own question: “How would I get my protein?” [25:08] — natural, goal-oriented query.
- **AI response quality:** Positive. “It did come back with increasing your protein intake, what it would do for you, tell you what a target would be, and then some good ways to do it.” [25:08]
- **SEQ rationale:** “I would say like a 5 because it was easy to find, but I have to get used to using AI, which I’ve just started using in the past couple of months.” [25:45] — **the 5 is about AI comfort, not UI design.**
- **Post-prompt engagement:** “The prompts afterwards, even like ideas that it will give you, like give me more meal ideas or what is a high protein snack. So I like that it answers that quickly.” [26:21]
- **Would use:** “To come up with recipes or snack ideas. Especially once it starts getting to know me as well, it will know what I would eat more of.” [26:56] — **AI personalization over time is a key expectation.**
- **Reveal — chat logging:** The AI **successfully logged her injection and side effects** inline. “I can put in like 0.25 milligram, nauseous… And then it told me it recorded it and the side effects of being nauseous. And then it also tells me ideas to help with the nausea, which is actually pretty good.” [28:06–28:24] — **⚠️ PL1 was inconsistent: chat logging WORKED for P04 but failed for P02. This is important context for the findings.**
- **Chat vs. UI preference:** Nuanced. “The screens feel more natural, but I like the idea of talking to the coach because I like the feedback.” [28:48] — **This is the most balanced response of any participant. She values the coaching/feedback layer the chat provides, even if screens are more intuitive for the mechanical act of logging.**

#### T5: Learning Pathways (29:42–35:30) | SEQ: 5

- **Did NOT find Learn independently.** Went to Meds first (“it’ll tell me when I did my injections”), then considered “the current dose” or “the coach.” [29:56–30:40]
- **Facilitator directed her to Learn tab.** [31:03]
- Once inside: “It’s very— it seems clear… It’s got— it’s very basic.” [31:16–31:25] — “basic” used positively here (approachable, not intimidating).
- Engaged with content: explored “Understanding your body” → “Map your cravings” (not active) → “Why your body works this way.” [31:53–32:09]
- **Navigation issue within Learn:** “I just couldn’t figure out how to get back out of it.” [32:56] — needed to scroll further to find back navigation. **Valid finding: in-lesson navigation is not intuitive.**
- **Would use:** “I’d probably read through it once. And then maybe not again.” Unless she hit a plateau. [34:45–35:00] — **consistent with other participants: Learn is valued as a reference, not a daily habit.**
- Structure makes sense. Nothing felt too basic or irrelevant.

#### T6: Evening Reflection (35:30–41:49) | SEQ: 7

- **Found evening wind-down card immediately.** “The evening wind-down… So reflect on your day.” [36:09–36:12]
- **Engaged thoughtfully.** Typed responses, went through full flow. Noted the AI response after saving: “And then it talks back to you.” [36:58]
- **Would use in real life:** “I am a big gratitude journal person, so at the end of the day I always do a gratitude journal of things that went well in that day. So I can go to bed positive and wake up in a positive way. So I would absolutely keep it like this. All in one place.” [37:44–38:00] — **THE strongest endorsement of reflections across all participants.**
- **Purpose:** “To keep your thoughts all in one area. So you know how you felt that day. And then you can reflect back.” [38:23] — also connected it to pattern recognition: “you can figure out why and kind of pull into why you emotionally ate or something like that.” [38:23]
- **Learning connection:** “It would show the difference of like why people eat certain ways or make excuses. If you followed that pathway, you’d be able to see the pattern.” [39:13] — one of only 2 participants to explicitly connect reflections to learning content.
- **Persona change noticed and appreciated:** “The insights are all different… for the evening it would let you know how your day went and give you motivation for the next day going forward, where the morning is asking you the basic questions.” [40:40–40:55] — **clearest articulation of the time-of-day adaptation value.**
- **Would want daily:** “Oh, I would like it. And I like that it changes through the day.” [41:37]

#### Backup: Meal Planning (41:49–45:43) | Only participant to fully engage

- Found it quickly: Nutrition → Plan → Generate meal plan. [42:03]
- Chose 3 days, all meals. “I’d probably go 3 days… I feel like if I plan too far in advance, I don’t actually do what I set myself out to do.” [42:24–45:11] — **practical insight on planning horizon.**
- **Gentle foods:** “I think it’s a great idea. I am one who gets nauseous on this injection, so I would love something that would give me ideas of gentle foods.” [43:24–43:31] — **the only participant to emotionally connect with this feature based on personal experience. ⚠️ Protocol note: The gentle foods toggle is contextual — it only appears in the meal plan when the planning window includes injection day + 2 days after. Both P04 and P06 selected 3-day plans, and the persona’s injection timing meant the 3-day window didn’t include the injection day, so the toggle never surfaced in the UI. The facilitator asked about gentle foods from a header label, not from the actual toggle. The concept resonated strongly with P04, but no discoverability conclusions can be drawn because the feature wasn’t actually present.**
- **Shopping list was the standout:** “I would use that. It would tell me exactly what I need to buy, and I don’t have to write it out myself and figure it out. Copy it, paste it into the Giant app, and I’m good to go.” [43:53–44:11] — **very concrete, real-world usage vision.**
- **Would use all features.** Would plan every couple of days. [44:46–45:03]
- **Trust in AI suggestions:** “It would get to know me if it’s using the AI. It would get to know what I like to eat.” [45:23] — again, personalization-over-time expectation.

#### Post-Session & Debrief (45:47–51:41)

- **How she’d describe it:** “I would say it’s a nutritional app, it’s a fitness app, it’s everything wrapped up in one. It even pulls recipes for you if you need it and helps you plan out your meals for the week, and I would highly recommend it.” [48:26] — **strongest endorsement of any participant.**
- **Most engaged:** Recipes. “I’m not one who likes to cook with more than 5 ingredients, so it’ll start to pick up on that and I would love it. I hate things that make me buy too much.” [49:09–49:21]
- **Comparison to MFP:** Liked MFP’s barcode scanning, but likes this app’s photo feature. [50:10–50:22]
- **Journal replacement:** Would replace her current handwritten gratitude journal with this app. Likes having “all in one spot.” [50:46–51:03]
- **Daily routine:** Would use morning and evening, block out 5-10 minutes. [51:15–51:23]
- **Would change:** Nothing (per facilitator data).

#### P04 Key Quotes for Report (with timestamps)

|Timestamp|Quote                                                                                                                                                     |Context                                |
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------|
|09:44    |“The coach — is it a tutorial? Is it a more descriptive part of the app? Is it something giving you pep? Pumping you up?”                                 |AI Coach labeling confusion            |
|14:03    |“Oh, I hit the wrong thing here”                                                                                                                          |Card icon/button affordance issue (F11)|
|15:22    |“It was a 7, but I did not know it was done until I knew it was done”                                                                                     |Meal logging completion ambiguity      |
|17:20    |“I will admit to being lazy for logging food. Putting it in every single piece of it takes so long that it turns me off”                                  |Photo vs. manual effort                |
|18:50    |“It’s too little. I would want to see what exactly it said, like one whole chicken breast or half an avocado. How many tomatoes?”                         |Nutritional detail request             |
|20:23    |“If I could take a picture of it, I would do it all the time”                                                                                             |Photo as adoption gatekeeper           |
|23:25    |“I just didn’t think about that. I wasn’t sure what the coach was”                                                                                        |AI Coach discoverability failure       |
|25:45    |“I would say like a 5 because it was easy to find, but I have to get used to using AI”                                                                    |SEQ reflects AI comfort, not UI        |
|26:56    |“Especially once it starts getting to know me as well, it will know what I would eat more of”                                                             |AI personalization expectation         |
|28:24    |“It told me it recorded it and the side effects of being nauseous. And then it also tells me ideas to help with the nausea, which is actually pretty good”|Chat logging worked + coaching value   |
|28:48    |“The screens feel more natural, but I like the idea of talking to the coach because I like the feedback”                                                  |Balanced chat vs. UI preference        |
|32:56    |“I just couldn’t figure out how to get back out of it”                                                                                                    |Learn in-lesson navigation issue       |
|37:44    |“I am a big gratitude journal person… I would absolutely keep it like this. All in one place.”                                                            |Reflections endorsement                |
|38:23    |“You can figure out why and kind of pull into why you emotionally ate or something like that”                                                             |Reflection + pattern recognition       |
|43:31    |“I am one who gets nauseous on this injection, so I would love something that would give me ideas of gentle foods”                                        |Gentle foods emotional connection      |
|43:53    |“The shopping list… Copy it, paste it into the Giant app, and I’m good to go”                                                                             |Meal planning real-world vision        |
|48:26    |“It’s a nutritional app, it’s a fitness app, it’s everything wrapped up in one… I would highly recommend it”                                              |Strongest overall endorsement          |
|49:09    |“I’m not one who likes to cook with more than 5 ingredients, so it’ll start to pick up on that”                                                           |AI personalization expectation         |

#### P04 Prototype Limitation Notes

- **PL1 (chat logging):** Inconsistent — chat logging **WORKED** for P04. She successfully logged an injection with dose and side effects via the AI Coach, and it also provided nausea management tips. This contrasts with P02, where the coach redirected to the + button. **The PL1 inconsistency itself is a finding: when chat logging works, the coaching feedback layer adds genuine value that UI-only logging doesn’t provide.**
- **PL3 (dose customization):** She considered changing the dose but accepted the pre-populated value when told it was simulated.

-----

*P01 summary pending — awaiting transcript upload.*

-----

### P01 — Female, 36, Wegovy (5 months), Calorie default

**Session duration:** 56:11 | **Moderator:** Jack | **Overall tone:** Low energy, concise, brutally honest — first session of the day (9am)

#### Warm-Up Context (00:00–08:15)

- App comfort: 7/7. Uses same apps consistently.
- Current tools: MyFitnessPal (calorie counting, not actively using), Apple Health (step counting, heart rate via watch).
- Key Apple Health complaint: **“It all just blurs together, like blends, it doesn’t really stick out.”** [06:52] — wanted icons/folders, more visual differentiation. Wished it was “more obvious.” [06:10] — **Ironic foreshadowing: this is the same visual differentiation problem the prototype has (F1).**
- Fiancé logs weight on a scale app. She doesn’t monitor that app herself.
- Currently just uses a weekly phone reminder for injections. No structured tracking.
- Heavy ChatGPT user (paid personal subscription + work license). This will be relevant to her AI Coach assessment.

#### T1: Home Screen Exploration (08:59–14:54) | SEQ: 7

- **First thing noticed:** Wellness score. “It piqued my curiosity.” Explored the breakdown (sleep, mood, nutrition, medication, activity). [09:33]
- Explored extensively — daily check-in, AI Coach (“that’s pretty cool”), scrolled, found + button and started to explore logging before being redirected to home screen.
- **One of only 2 participants to notice the + button.** “It’s kind of self-explanatory because it has the plus sign… if I need to add something or log something, I would be hitting the plus sign.” [18:22] — she’s the exception that proves the rule on F1.
- **Noticed everything:** wellness score, cards, insight cards, Coach, + button. Most thorough home screen exploration of all participants.
- Could articulate purpose: “It’s like an all-in-one… for any type of health needs you would need, like aside from needing a physician.” [12:43]
- Positive standout: “I like how you can log everything here… I like the Coach as well. I’m big into the AI stuff.” [14:26–14:45]

#### T2: Log Medication (16:43–21:26) | SEQ: 7

- **Entry path: + button.** The ONLY participant to use the + button for medication logging across all 7 sessions. [17:08]
- Tried to change dosage — prototype limitation. **⚠️ PL3.** [17:08]
- **Confirmation confidence: 7.** “Given that this would be an app that I could trust… I got the confirmation. So if I went back and it’s not there, then I would say the app sucks.” [19:12] — blunt but telling. Trust is contingent on the confirmation being truthful.
- Body map: 7. “It was better than expected… typically it would just be like, yes, today, right arm.” [20:07–20:14]
- Also noted that the body map shows injection location options she had previously looked up herself. “At one point I did look up like the different spots where you could inject, so that would be helpful.” [20:25]
- **Comparison:** Currently just sets a weekly reminder. This app would help her keep detailed records for doctor visits: “Even if the doctor asks like, ‘Oh, what day?’ And I’m assuming you can put side effects… opposed to just like, ‘Yeah, everything is good,’ when it’s like, ‘No, some things did happen, you just forgot.’” [21:30] — **strong real-world use case.**

#### T3: Log a Meal (22:26–30:10) | SEQ: 7

- **Input method: Typed description.** The ONLY participant who did not photograph the image. “This is not my type of meal, so I don’t know what this is called… I’m gonna do a description. I have AI tell me what this is.” [22:59]
- Described ingredients in detail: “grilled chicken with the dressing, drizzled with cherry tomatoes, shredded carrots, sliced avocado, maybe arugula in a bowl.” [23:10–23:47]
- Assigned origin: “I bought this from Costco.” [23:56]
- **Why she chose describe over photo:** “Because that was the easiest for me out of those options, based on what the meal was.” Also: “I use a lot of AI tools daily. So that was just an easy one for me.” [25:16–25:34] — **her AI fluency made text input feel natural, while most participants found photo easier.**
- Liked that there were multiple options: “I didn’t know it would have, where you could describe it. So that was cool.” [24:58]
- **Nutritional accuracy:** Yes, about right level of detail. [25:52, 26:09]
- **Display preference:** Preferred calorie view. Macro/whole-foods view was “more confusing.” “I don’t know what they’re talking about with the mixed and the whole.” The calorie view “made sense to me without having to learn what this is.” [27:42–28:11] — **learning curve is the barrier, not preference for less info.**
- **Toggle:** Values having the option, “as long as it’s not in the way.” [29:16–29:27]
- Would track daily: “Yeah, I would do it. Just to stay on top of everything.” [29:50]

#### T4: AI Chat (30:21–42:14) | SEQ: 5

- **Part A — Did NOT find AI Coach for summary.** Navigated around for ~60 seconds before the facilitator guided her to the Coach. [31:30–31:56]
- Interesting: she HAD explored the Coach during T1 (“I like the Coach, I’m big into the AI stuff”) but did NOT go there when asked to find a summary/progress view. **Recognition-vs-recall gap** — same pattern as P05 with Learn.
- **First instinct was Progress screen** (the “analysis thing” icon). “I wasn’t expecting it to be like the analysis thing.” [35:01]
- **Expected a calendar icon for progress:** “I was looking for like a calendar.” [35:37] — **same suggestion as P03’s post-session recommendation for progress as calendar with arrows.**
- **SEQ: 5.** “Not that there’s something wrong with it, it’s just not what I was expecting.” [35:37]
- **Once in Coach:** Typed “Is there a certain time of day you should take the injection?” [32:48] — practical, real-world question.
- Used follow-up prompts: “What if I miss a dose?” — found the answer helpful. “I didn’t know that.” [33:27–33:43]
- **Key value insight:** “This is helpful overall just to be able to ask those questions without having to call your doctor.” [33:43]
- Would use the AI Coach, BUT: “The only reason I probably wouldn’t is because I have my platform that I use and pay for… depending on the scope of what you can ask this thing, maybe eliminate one.” [37:44] — **ChatGPT is a direct competitor in her mind.** This is unique to P01 among all participants.
- **Reveal — chat logging:** Attempted to log injection via chat. Tried to customize dose/time/side effects in the chat. Hit limitations. **⚠️ PL1/PL3.** “I wasn’t able to customize how I want it.” [42:22]
- **Chat vs. UI preference:** UI screens directly. “It’s just right there… in the world of convenience, who wants to type when you don’t have to?” [41:51]

#### T5: Learning Pathways (42:33–47:26) | SEQ: 7

- **Did NOT find Learn immediately.** Went to Meds first, then Coach Insights, then “there’s a Learn tab.” [42:56–44:12] — detour but self-corrected.
- Once inside: “Oh yeah, it has information here how GLP-1s work. Your first injection. Oh yeah, it tells you everything you need to know.” [44:12–44:30]
- Engaged with a lesson (3 brain systems — gatekeeper, co-governor, executive). Found it helpful: “That’s helpful with the brain information… the chart explaining it even further.” [45:36–45:53]
- **Purpose:** “Give you knowledge and probably fill in those gaps of those questions that people have about the medication.” [46:40]
- **Would use:** “If I had those questions, yes… opposed to Googling it, just going there instead.” [47:06–47:26]

#### T6: Evening Reflection (47:42–53:01) | SEQ: 7 (ease of finding) / Effective refusal

- **Did NOT find reflection prompt initially.** Went to Progress (“your journey”). Reviewed individual categories (nutrition, hydration, steps, sleep). [48:28–49:14]
- Facilitator asked if she noticed a reflection activity. “Oh yeah, reflect.” [49:51] — she SAW it but hadn’t processed it as relevant to “checking in with yourself.”
- **Immediate refusal:** “Yeah, I probably wouldn’t want to do this.” [50:06]
- **Why:** “It’s too tedious.” [50:11]
- Facilitator asked her to try. She started, then: **“I hate this.”** [51:46] — the most visceral negative reaction of any participant to any feature.
- Facilitator stopped the task.
- **Purpose understood correctly:** “Probably to just give you some positive things to end your day with.” [52:05]
- **Concession:** “Maybe if I’m needing that at one evening, I would do it.” [52:05] — acknowledges situational value.
- **Core objection:** “Typing that in just to get some feedback from an app personally is not— it’s not for me. It’s not rewarding for me.” [52:05–52:39]
- **What she’d prefer:** “I’d rather be like, babe, I’m feeling down, tell me something to make me feel better… talk to a human.” [52:39–52:50] — **the reflection feature is competing with human connection for this user, not with other app features.**
- **Despite all of this:** “I actually like [the app] though.” [53:01] — her rejection of reflections did not color her overall perception of the app.
- **SEQ: 7** for ease of finding/using it. The feature works; she just doesn’t want it.

#### Post-Session & Debrief (53:05–56:09)

- Session ran to the hour mark. **Debrief was truncated** — only the questionnaire was completed, no detailed debrief questions.
- **Would change:** “The evening wind down.” (from facilitator data)
- **Most valuable feature:** “The knowledge it provides about the medication taken and the ability to log the injections as well as any side effects.” (from facilitator data)
- Final thought: “No, I’m good.” [56:06]

#### P01 Key Quotes for Report (with timestamps)

|Timestamp|Quote                                                                                                                                             |Context                                             |
|---------|--------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------|
|06:52    |“It all just blurs together, like blends, it doesn’t really stick out”                                                                            |Apple Health UI complaint — parallels prototype’s F1|
|09:33    |“It has a wellness score here, so that piqued my curiosity”                                                                                       |First thing noticed                                 |
|11:48    |“Everything is categorized here. I like that.”                                                                                                    |Home screen positive impression                     |
|14:45    |“I like the Coach as well. I’m big into the AI stuff”                                                                                             |AI enthusiasm                                       |
|18:22    |“It’s kind of self-explanatory because it has the plus sign… if I need to add something or log something, I would be hitting the plus sign”       |Only participant to articulate + button purpose     |
|19:12    |“Given that this would be an app that I could trust… I got the confirmation. So if I went back and it’s not there, then I would say the app sucks”|Trust contingent on confirmation accuracy           |
|20:07    |“It was better than expected… typically it would just be like, yes, today, right arm”                                                             |Body map delight                                    |
|21:30    |“Even if the doctor asks… opposed to just like, ‘Yeah, everything is good,’ when some things did happen, you just forgot”                         |Real-world use case for tracking                    |
|22:59    |“This is not my type of meal… I’m gonna do a description. I have AI tell me what this is”                                                         |Why she typed instead of photographing              |
|25:34    |“I use a lot of AI tools daily. So that was just an easy one for me”                                                                              |AI fluency driving input method choice              |
|27:42    |“This is more confusing. I don’t know what they’re talking about with the mixed and the whole”                                                    |Macro view learning curve                           |
|33:43    |“This is helpful overall just to be able to ask those questions without having to call your doctor”                                               |AI Coach value proposition                          |
|35:37    |“I was looking for like a calendar”                                                                                                               |Expected progress icon                              |
|37:44    |“The only reason I probably wouldn’t is because I have my platform that I use and pay for”                                                        |ChatGPT as AI Coach competitor                      |
|41:51    |“In the world of convenience, who wants to type when you don’t have to?”                                                                          |UI over chat for logging                            |
|50:06    |“Yeah, I probably wouldn’t want to do this”                                                                                                       |Reflection refusal                                  |
|51:46    |“I hate this”                                                                                                                                     |Visceral reflection rejection                       |
|52:39    |“It’s not rewarding for me”                                                                                                                       |Core reflection objection                           |
|52:50    |“I’d rather be like, babe, I’m feeling down, tell me something to make me feel better… talk to a human”                                           |Reflection competing with human connection          |
|53:01    |“I actually like [the app] though”                                                                                                                |Rejection of one feature ≠ rejection of app         |

#### P01 Prototype Limitation Notes

- **PL3 (dose customization):** Tried to change dose in both UI logging and chat logging. Noted as expected feature.
- **PL1 (chat logging):** Attempted to customize injection details via chat but hit limitations. “I wasn’t able to customize how I want it.” Hard to separate PL1 from PL3 here.

#### P01 Analytical Notes

- **The Apple Health complaint is a gift for the report.** She described the exact problem the prototype has (“it all blurs together”) when talking about a different app. This creates a powerful narrative frame: users already know what bad visual differentiation feels like, and they’ll hit the same wall here if F1 isn’t addressed.
- **Her AI fluency is an outlier.** She’s the only participant who typed a meal description instead of photographing it, and the only one who positioned ChatGPT as a competitor to the AI Coach. Her data should be weighted accordingly — she represents a real but unusual user segment (power AI users who already have established AI workflows).
- **The “I hate this” / “I actually like it though” juxtaposition is the strongest evidence that reflections are a segment feature, not a universal one.** Her rejection was total and personal, but it didn’t damage her perception of the app. The report should frame reflections as high-value-for-some, not try to universalize them.

-----

*P03 summary pending — awaiting transcript upload.*

-----

### P03 — Female, 54, Wegovy (6 months), Calorie default

**Session duration:** 53:22 | **Moderator:** Jack | **Overall tone:** Practical, direct, self-aware — the most experienced health app user and the most consistently critical scorer

#### Warm-Up Context (00:00–07:05)

- App comfort: 6/7. Tries new apps regularly.
- Current tools: Weight Watchers (liked the routine, learned tracking quickly — but quit because of cost), Healthi (cheaper alternative, “doesn’t do quite as much,” still learning it).
- Key WW insight: She valued the **routine** of tracking, not just the features. And cost was the deciding factor to leave. [05:27–05:52]
- Healthi’s advantage: “It’s not that point-based thing. It’s strictly macros and calories… more universal.” [06:45–06:59]
- **This is the most experienced health app user in the group.** She has real benchmarks to compare against.

#### T1: Home Screen Exploration (09:07–13:02) | SEQ: 6

- **First thing noticed:** Wellness score. “Wonder what that means.” [09:37] — curiosity but not immediate understanding.
- Also noticed: headache check-in (“I wouldn’t even think that would be something to think about”), food/sleep/steps logging, coach, easy spots to log.
- Could articulate app purpose: “Keeping track of your nutrition and activity and sleep and mood all in one spot.” [11:30]
- **Surprised by sleep tracking** on a weight loss app: “My watch does that. I’ve never thought to relate it to weight loss.” [12:26–12:34] — **interesting insight: the holistic wellness framing was unexpected for her.**
- **Did NOT notice + button or tab bar during exploration.**
- SEQ 6 (not 7): slightly lower than most, consistent with her generally more critical stance.

#### T2: Log Medication (13:02–17:45) | SEQ: 4

- **Initially went to meds screen.** “I would assume I would hit this meds button… I don’t see a spot to say you’re doing it.” [13:19–13:31] — tried tapping on calendar, injection site info, dose editing. None were logging entry points.
- **Self-corrected:** Scrolled down and found “log injection” card. “Log injection is right there.” [14:01–14:22]
- **SEQ: 4.** “Because I went to the wrong spot first.” But immediately added: “It wasn’t necessarily the app’s fault.” [14:55–14:59] — **she penalizes her own score for the navigation error even while acknowledging it’s not a design flaw.** This self-awareness makes her low scores more nuanced than they appear.
- Why meds first: “Because they were just right up there on the top. I didn’t bother to scroll.” [15:24–15:27]
- **Confirmation confidence: 7.** Also noticed the card disappeared after logging. [16:05]
- Body map: 7 usefulness. “She had that nice little map. And it kept track of where you had previously injected.” [16:57]
- **Learning transfer:** She explicitly applied her T2 mistake to T3: “Well I learned not to hit those.” [18:03] — **demonstrates rapid adaptation.**

#### T3: Log a Meal (17:45–25:19) | SEQ: 5

- **Input method: Photographed the image.** Saw the options (“select from recipes, take a photo, or describe what you ate”) and chose photo: “I’m going to try taking a photo.” [18:03]
- **The Panera incident:** After photo analysis identified “grilled chicken salad,” she selected that she bought it and chose Panera. But when it showed Panera’s specific menu items, she backtracked: “I’m going to go back because no, that is not that… I would want accurate results. I wouldn’t want to say it’s a Green Goddess dressing salad from Panera if it isn’t.” [18:50–20:37] — **this is a data integrity instinct, not a UI failure. She cared more about accuracy than speed.**
- **SEQ: 5.** “Again, user error. Tried to skip a step by just saying I bought it.” [20:19–20:23] — again, she self-attributes the difficulty.
- Nutritional accuracy: Yes. Detail level: “Exactly” right amount. [22:26, 22:34]
- **Display preference: Calorie view.** “Personally, there would be very little processed foods anyway with me. So I don’t worry too much about that. But we definitely worry about the calories.” [23:31–23:36]
- Toggle: Would pick one and stick. [24:19]
- **Key feature request — saved/favorited meals:** “I would like if standard meals were saved. That’s something Weight Watchers did. I usually eat the exact same thing every breakfast, so I would just say, yeah, I had my breakfast. And click.” [24:40–24:54] — **directly informed by WW experience. This was also captured in the end-of-day suggestions.**

#### T4: AI Chat (25:19–33:19) | SEQ: 4

- **Part A — Found AI Coach, but continued looking.** Clicked wellness score first (“looks like that’s just for today”), then went to Coach and checked progress. But then went back to homepage looking for a weekly summary elsewhere. [25:47–26:56]
- **Key frustration:** She wanted a dedicated summary button on the homepage: “I would love if there was just a button on the front that could bring all of these things into one. For the week.” [29:44] — Why a button over AI? **“It’s quicker. You don’t have to actually type a question.”** [30:07–30:09] — **this is the clearest articulation of the AI Coach friction: it requires effort (typing) for something that should be instant (viewing).**
- When she did ask the AI “how many calories should I plan for dinner?” — **“I love it, love it. Look at that, it gives you some ideas for dinner.”** [27:54] — genuine delight with AI responses for food-related queries.
- Also typed “weekly summary” into the chat and got a comprehensive response: “It gives you everything, your side effects, your food choices, and your mindset.” [28:42]
- **SEQ: 4.** “I think I figured out that I could get it from the coach. I just was looking to see if there was some other place.” [29:22–29:26]
- **Would absolutely use the AI Coach.** “I personally use ChatGPT for everything, so I liked that.” [30:30]
- **Chat logging worked** — typed “log my injection,” got prompted for location, logged successfully. “It says great.” [31:50–32:07] **⚠️ PL1: Worked for P03 (also worked for P04, failed for P02).**
- **Chat vs. UI preference:** “I think it’s the same either way.” But noted: “This didn’t say, oh, you injected here last time. This just said, where did you inject? So might prefer someone reminding me.” [32:15–32:21] — **the body map’s historical context is a UI-only advantage the chat lacks.**

#### T5: Learning Pathways (33:19–38:30) | SEQ: 7

- **Found Learn immediately.** “There’s a learn button right there.” [33:47] — direct navigation, no detour.
- Explored content: “Looks like they’re short little courses like getting started, how does it work, first injection. Nausea. Moving up. This is great information that you don’t always have.” [33:47]
- Noticed the pathway structure: “They give you a path to work through with a lot of reading and a spot to complete once you finished it… a little trophy when you finish.” [36:00–36:21]
- **Would NOT spend time on it personally:** “It took me a long time to navigate to where I currently am [in life]. And I don’t know that I would have much need for any of this.” [36:49–37:01]
- **But for newer users:** “For somebody who is new, absolutely.” [37:13]
- **Content felt too basic** for her stage of journey. [38:54]
- **Would come back if stuck:** “Maybe if I was in a slump or needing some tools to move further.” [38:09]
- **Connected reflections to learning content:** “Especially since a lot of the learning content was about your mindset and managing your habits and controlling mind over body. And I think this would help you reflect on how you’re doing with that.” [43:27] — **one of only 2 participants to make this explicit connection.**

#### T6: Evening Reflection (39:23–45:10) | SEQ: 7

- **Found evening wind-down card immediately.** “I see this evening wind down, reflect on your day.” [40:07]
- **Rushed through:** Typed “yes” for each prompt. [40:07–40:47] — minimal engagement. Facilitator observed this.
- **Format assessment:** “It’s natural to ask the questions. Whether I would have an answer, I don’t know.” [41:18] — **the questions are good; the habit of reflection doesn’t exist for her.**
- Why not: “You have to— I don’t think about what’s going on in my day. I just go through it.” [41:27] — but then: “It might be good to stop and think.” [41:34] — **she sees the theoretical value even though she wouldn’t do it.**
- **Would not use daily.** Nothing would change that. “Kind of ambivalent. It’s there.” [44:58]
- **Purpose:** “Encouragement. Letting a person know that, hey, you might have not had the best day, but you’re doing good.” [42:46–42:51]
- **Persona change noticed:** “Looks busier… you have all these insights now saying, you know, this is stuff to think about tomorrow.” [44:13–44:16]

#### Post-Session & Debrief (45:19–53:17)

- **Would change:** Progress visibility. Wanted protein status right next to wellness score on home screen. [48:49–49:06]
- **Wellness score reaction:** “The Wellness Score is kind of almost like a gimmick to me.” [49:26] — **strongest negative reaction to the wellness score of any participant. But importantly, she framed it as: the score itself is less useful than the underlying data (especially protein).**
- **Most valuable feature:** “The ease of logging what you’re eating.” [50:07]
- **Would replace current app:** “I would definitely consider replacing the one I use with this and use this instead.” [52:34] — high praise from the most critical participant.
- **Genuinely useful feature not seen elsewhere:** “The AI thing. It would keep me from going somewhere else to ask the questions.” [51:56]
- **How she’d describe it:** “A way to keep track of your whole health in one app, including your eating.” [50:30]

#### P03 Key Quotes for Report (with timestamps)

|Timestamp|Quote                                                                                                                 |Context                                         |
|---------|----------------------------------------------------------------------------------------------------------------------|------------------------------------------------|
|12:34    |“My watch does that. I’ve never thought to relate [sleep] to weight loss”                                             |Holistic wellness framing unexpected            |
|14:55    |“Because I went to the wrong spot first. But it wasn’t necessarily the app’s fault”                                   |Self-aware scoring on T2                        |
|18:03    |“Well I learned not to hit those”                                                                                     |Learning transfer from T2 to T3                 |
|20:37    |“I would want accurate results. I wouldn’t want to say it’s a Green Goddess dressing salad from Panera if it isn’t”   |Data integrity instinct                         |
|24:40    |“I would like if standard meals were saved. That’s something Weight Watchers did”                                     |Saved meals feature request                     |
|27:54    |“I love it, love it. Look at that, it gives you some ideas for dinner”                                                |AI Coach delight on food queries                |
|29:44    |“I would love if there was just a button on the front that could bring all of these things into one”                  |Summary button request                          |
|30:09    |“It’s quicker. You don’t have to actually type a question”                                                            |Why button > AI for summaries                   |
|33:47    |“This is great information that you don’t always have”                                                                |Learning content value                          |
|36:49    |“It took me a long time to navigate to where I currently am… I don’t know that I would have much need for any of this”|Learning content too basic for experienced users|
|41:18    |“It’s natural to ask the questions. Whether I would have an answer, I don’t know”                                     |Reflections — good questions, no habit          |
|41:34    |“It might be good to stop and think”                                                                                  |Concession on reflection value                  |
|49:26    |“The Wellness Score is kind of almost like a gimmick to me”                                                           |Wellness score critique                         |
|50:07    |“The ease of logging what you’re eating”                                                                              |Most valuable feature                           |
|51:56    |“The AI thing. It would keep me from going somewhere else to ask the questions”                                       |AI as consolidator                              |
|52:34    |“I would definitely consider replacing the one I use with this”                                                       |Would replace Healthi                           |

#### P03 Prototype Limitation Notes

- **PL1 (chat logging):** Worked successfully. She typed “log my injection” and it completed the flow. Chat logging now confirmed working for P03 and P04, failed for P02 only.

#### P03 Analytical Notes

- **Her low SEQ scores are systematically self-penalizing.** She gave 4 on T2 and 5 on T3 while explicitly stating it wasn’t the app’s fault. In the report, these scores should be contextualized: the raw numbers understate usability because she’s grading her own navigation performance, not the UI. The real T2 issue is the meds-screen mental model mismatch (F6), which she identified perfectly.
- **The learning transfer is powerful report material.** She made a navigation mistake in T2, then explicitly avoided repeating it in T3 (“I learned not to hit those”). This shows the app has a fast learning curve even when initial discoverability is imperfect.
- **P03’s wellness score feedback is about interaction patterns, not validation.** The wellness score is a visual flourish that abstracts data and provides gamification to make holistic wellness approachable. It doesn’t need to resonate with everyone. The more compelling finding is HOW participants interacted with it: P03 wanted raw metrics (protein) surfaced alongside it; P04 assumed it would function as a weekly summary; P06 noticed it immediately because of its visual prominence. The report should focus on wellness score interaction patterns (what people tap, what they expect to find, what they want surfaced from it) rather than whether the concept is “good” or “gimmicky.”
- **Her progress summary request (“a button on the front”) aligns with P01’s “calendar icon” expectation.** Two participants independently asked for a quicker, non-AI path to their weekly summary. This is a real design gap, not just AI discoverability — it’s about **effort-to-insight ratio** for routine status checks.

-----

*P05 summary pending — awaiting transcript upload.*

-----

### P05 — Female, 61, Zepbound + methotrexate + Enbrel (1 year), Calorie default

**Session duration:** 61:26 | **Moderator:** Jack | **Overall tone:** Extremely talkative, enthusiastic, stream-of-consciousness — the oldest participant and the richest source of think-aloud data

#### Warm-Up Context (00:00–09:58)

- App comfort: 7/7. Tries new apps regularly but also returns to established ones.
- Current tools: Shotzy (free version — tracks GLP-1 injections, weight, injection sites), ResMed (CPAP machine usage), Apple Watch (sleep tracking), Medicare Advantage Healthy Rewards app.
- Shotzy strengths: Free, tracks injection sites and weight weekly, bar graph trend. Paid version tracks more but she doesn’t need it. [05:57]
- **Key Shotzy gap:** “It gives you options, but I actually have to go back and look to see where I injected last time… it doesn’t tell me where the last injection was. I have to go and look that up.” [22:44–23:07] — directly parallels the body map advantage.
- On multiple injectable medications (Zepbound, methotrexate, Enbrel) — most complex medication profile of any participant.
- **Does not typically use AI.** “I don’t usually use AI.” [35:42] — important context for her T4 experience.

#### T1: Home Screen Exploration (09:58–18:25) | SEQ: 7

- **Most extensive exploration of any participant.** Spent ~8 minutes exploring organically, touching nearly every feature.
- First impression: “This looks like it kind of combines a lot, like more than one app.” [10:40] — immediately saw the consolidation value.
- **Noticed behavioral support angle:** “Has like kind of behavior modification or like a support kind of thing built into it?” [11:23] — one of the few participants to identify the behavioral science framing unprompted.
- **FOUND LEARN TAB during exploration.** “Oh, that’s— I don’t know how to get back to— oh, that was Learn Coach.” [11:41] — she navigated to Learn during open exploration but didn’t register it as a distinct section. **This is the recognition moment that precedes the recall failure in T5.**
- Also noticed: photo meal logging (“I know there are apps that’ll do that, but it’s interesting that’s all in one app”), sleep tracking (wondered about wearable device integration), injection site map (“I like that”), water tracking, calorie tracking.
- Found the progress arrow during exploration: “4.2 pounds this week. So I like that.” [17:05+]
- Could articulate purpose: “Tracking health information, specifically if you’re on a GLP-1. But it also tracks your sleep, your activity, your nutrition, in addition to the medication itself.” [16:27]

#### T2: Log Medication (18:25–23:19) | SEQ: 7

- **Initially went to meds screen.** “Go to the meds. It has it scheduled for, like, the little dots around it. Current dose. Pressing on the schedule does not give you the, like, today’s information.” [18:40–19:04] — same meds-screen error as P03, P07.
- **Self-corrected** to home screen injection card. “It said injection day, medication, log injection.” [21:31]
- Logged successfully. Noted the time selection and backdating options. [19:31]
- **Body map: 7.** “I like that it tells you where your last one was because in the app I use, it gives you choices, but I actually have to go back and look.” [22:21] — direct comparison to Shotzy, same pain point.
- **Comparison:** Body map is a clear advantage over Shotzy: “It doesn’t tell me where the last injection was. I have to go and look that up.” [22:49]

#### T3: Log a Meal (23:19–31:57) | SEQ: 7

- **Input method: Photographed the image.** “Take a photo… That’s really cool, actually.” [24:08–24:26] — genuine delight.
- Photo recognition worked: identified meal, gave restaurant match options (78% confident). She selected a match.
- Noticed calorie tracking and protein tracking. “I’m not sure if mine does that or not, but I don’t usually do that because I’m not really OCD about that. I’m just trying to be healthier first.” [12:34] — earlier during exploration.
- **Nutritional accuracy:** Yes. Detail level: “For me, that would be fine.” Acknowledged others might want more (keto/macro users). [27:21]
- **Display preference: Nuanced — the only participant who waffled.** Initially said calorie view, then reconsidered: “I don’t really know if it would matter for me because I’m not counting calories, but I am trying to keep track of my protein. So this [macro view] showing the protein might be a better fit.” [31:10–31:21] — **per the rainbow grid she’s marked as preferring macro, which aligns with this final answer, but the transcript shows genuine ambivalence.**
- Toggle: Would pick one and stick personally, but can see others switching. [31:03]
- Noticed the wellness score changed after logging. [27:54]

#### T4: AI Chat (32:00–43:56) | SEQ: 6

- **Part A — Did NOT find AI Coach independently.** Went to home screen, looked at activity streaks, then found the progress arrow. [32:24–34:03] — found progress summary but not via Coach.
- **Facilitator guided her to AI Coach.** “I want to show you one more feature. This is the AI Coach.” [34:42]
- **First interaction:** Tried the microphone (non-functional). **⚠️ PL2.** Then typed “How am I doing?” [34:58–35:30] — natural, conversational query.
- **Immediate positive reaction:** “That’s pretty cool. And it like addresses you too, like with your name.” [35:30]
- Why she didn’t think of AI Coach: “I’m not used to all of the things that are the potential that there is for it or that it can do.” [36:40–36:49] — **not a UI problem, but an AI literacy gap.**
- **Emotional connection:** “Because I personally don’t have anyone that I’m going through like a weight loss journey with. So it’s just me, myself, and I. Having something like that is pretty interesting.” [38:22] — **the strongest emotional rationale for the AI Coach from any participant. She sees it as a companion.**
- **Would use, but uncertain about novelty:** “I don’t know if the novelty would wear off, but when I need a kick in the pants or a motivator, that would be definitely nice to have.” [38:38]
- **Reveal — chat logging:** Successfully logged injection via chat. Liked the coaching feedback: “It was like kind of having like a friend guide you through the whole thing and giving you feedback.” [42:06] But would prefer the body map UI for routine logging once experienced: “If I was first starting out on the medication, I would prefer that because it gives you coaching. But once you’re in the rhythm, then just going to the body diagram.” [42:29] — **the most nuanced chat-vs-UI preference of any participant. She sees a temporal arc: chat for onboarding, UI for maintenance.**
- Also noticed the patient information leaflet reference in the chat: “It has like a patient guide loaded into it… that’s a lot easier than pulling out a little brochure.” [43:28–43:49]

#### T5: Learning Pathways (44:04–53:37) | SEQ: 4 (to find)

- **THE recognition-vs-recall failure.** She found Learn during T1 exploration [11:41] but could NOT find it during the directed T5 task.
- **Facilitator asked FIVE times** about learning/education:
1. “See if the app offers anything that could help you learn more in your medication journey.” [44:04] → She went to AI Coach
1. “See if the app offers anything that could help you learn more about anything as you go along.” [44:37] → Still in AI Coach
1. “See if the app offers anything to help you understand and learn more.” [45:01] → Still looking at Coach suggestions
1. “Is there anything in the navigation that might be related to learning or education?” [46:38] → “Well, I think the going to the coaching, the AI coaching.”
1. “Is there anything outside of the AI coaching that might be related to learning or education?” [46:56] → Listed home screen insights about hydration, protein timing. “There’s a lot of education on here.”
- **Finally found it:** “Oh wait, hold on. Learn. Okay. Duh. Yeah. Okay.” [47:45] — **the “duh” is significant. She recognized it instantly once she looked at the bottom nav. The problem wasn’t that Learn is hidden — it’s that the bottom nav doesn’t register as a navigation element.**
- **Her explanation:** “I kept keying on the home key and then like nutrition was already mentioned above. The coach was already mentioned above. I guess I just didn’t even think to look along the bottom to see that there was like a learning section.” [49:25] — **THE smoking gun quote for F1. She explicitly describes the bottom nav as invisible to her mental model. She was looking at the home screen content and the features mentioned within it, not the navigation frame.**
- Once found: engaged well. Explored metabolism section, noticed personalized path, noticed 63 items available. [48:10]
- **Would use:** “Maybe initially… once you go through it, then I don’t know if I would go back and review it.” Would go through all of it at least once. [52:41–53:15]
- **Purpose:** “Kind of be a support, like, behaviorally. It’s like supplementary to doctor visits.” [50:41, 52:06]

#### T6: Evening Reflection (53:39–58:22) | SEQ: 6

- **Found evening reflection card on home screen.** “It has reflect.” [54:26]
- **Noticed the CBT framing:** “Cognitive therapy, evening reflection consolidates learning and improves next day decision-making.” [54:26] — one of the few participants to read and comment on the behavioral science context.
- **Initial resistance, then engagement:** “I felt forced initially, but I think if you’re using it, it would become natural.” [56:35] — acknowledged the habit barrier honestly.
- Typed genuine responses (not placeholder text): “I wanted chocolate, but I made a better choice.” [55:45]
- **AI personalization impressed her:** “It’s really pretty cool how the AI part customizes to what I said. Like, I talked about chocolate, I talked about that.” [56:13] — she noticed the AI reflection response was personalized to her inputs.
- **Would use with effort:** “I would have to make a conscious effort to start doing, but if I got started doing it and it made me feel good, that it would probably be something I would continue.” [57:17] — **conditional adoption: needs initial push, then self-reinforcing if the experience is positive.**
- **Purpose:** “To keep you in touch with your feelings as you’re on the weight loss journey. It’s like a positive reinforcement.” [57:55]
- Also: “If it’s not positive, then… it might be like just a cheerleader for tomorrow.” [58:15]

#### Post-Session (58:22–61:23)

- **Pricing question:** Asked if the app would be a paid purchase. Suggested a 7-day trial period to let people experience it before committing. [60:38–60:57] — **unprompted business model feedback.**
- **No detailed debrief** — session ran long (61 min), moderator wrapped up.

#### P05 Key Quotes for Report (with timestamps)

|Timestamp|Quote                                                                                                                                                 |Context                                         |
|---------|------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------|
|10:40    |“This looks like it kind of combines a lot, like more than one app”                                                                                   |App consolidation value                         |
|11:23    |“Has like kind of behavior modification or like a support kind of thing built into it?”                                                               |Identified behavioral science framing unprompted|
|22:21    |“I like that it tells you where your last one was because in the app I use, I actually have to go back and look”                                      |Body map vs. Shotzy comparison                  |
|24:26    |“That’s really cool, actually”                                                                                                                        |Photo meal logging delight                      |
|35:30    |“That’s pretty cool. And it like addresses you too, like with your name”                                                                              |AI personalization noticed                      |
|36:49    |“I’m not used to all of the things that are the potential that there is”                                                                              |AI literacy gap                                 |
|38:22    |“I personally don’t have anyone that I’m going through like a weight loss journey with. So it’s just me, myself, and I”                               |AI Coach as companion                           |
|42:29    |“If I was first starting out, I would prefer [chat] because it gives you coaching. But once you’re in the rhythm, then just going to the body diagram”|Temporal chat-vs-UI preference                  |
|43:49    |“That’s a lot easier than actually pulling out a little brochure and having to look through it”                                                       |Patient info leaflet in chat                    |
|47:45    |“Oh wait, hold on. Learn. Okay. Duh”                                                                                                                  |Learn tab recognition-vs-recall moment          |
|49:25    |“I kept keying on the home key… I guess I just didn’t even think to look along the bottom to see that there was a learning section”                   |**F1 smoking gun — bottom nav invisible**       |
|56:13    |“It’s really pretty cool how the AI part customizes to what I said”                                                                                   |Reflection AI personalization                   |
|57:17    |“I would have to make a conscious effort to start doing, but if it made me feel good, I would probably continue”                                      |Conditional reflection adoption                 |
|60:57    |“If it had like a trial kind of period… then it might be like, oh, this is pretty cool, I would like to continue”                                     |Business model suggestion                       |

#### P05 Prototype Limitation Notes

- **PL2 (microphone):** Tried the mic in AI Coach. Non-functional. She doesn’t typically use AI and was confused about how to interact initially. The non-functional mic added to her uncertainty.

#### P05 Analytical Notes

- **The T5 Learn failure is the single strongest evidence for F1 in the entire dataset.** She found Learn during exploration, couldn’t find it during directed use, and explicitly explained why: the bottom nav doesn’t register as a navigation element. Her five-attempt search, with the facilitator progressively narrowing the hint, is a textbook usability testing moment. It should be a centerpiece of the F1 finding in the report, ideally with a visual showing the progression of prompts.
- **The “buddy” framing for AI Coach is unique and emotionally resonant.** No other participant framed the AI this way. For someone without a weight loss support network, the AI Coach fills a social/emotional gap, not just an informational one. This is powerful positioning material for the app’s value proposition.
- **Her temporal chat-vs-UI model (chat for onboarding, UI for maintenance) is the most sophisticated preference articulation in the dataset.** It reconciles the apparent contradiction of “chat is valuable” AND “I prefer the UI” — they serve different needs at different stages of the user journey.
- **The pricing question is an unsolicited signal of purchase intent.** She didn’t ask “would I have to pay for this?” (resistance) — she asked “is this something you would purchase?” (interest). Her trial period suggestion is practical business model feedback.

-----

*P06 summary pending — awaiting transcript upload.*

-----

### P06 — Female, 36, Zepbound (2 months), Macro default

**Session duration:** 56:21 | **Moderator:** Allison | **Overall tone:** Articulate, candid — has type 1 diabetes and uses Dexcom CGM, giving her more health app exposure than most participants

#### Warm-Up Context (00:00–06:11)

- App comfort: 6.5/7. Tries new apps regularly.
- Current tools: iPhone Health (steps, blood pressure, heart rate, quizzes, articles), Dexcom (continuous glucose monitor for type 1 diabetes — diagnosed very young), Life app (menstrual cycle), daily motivational quote app for mental health.
- **Type 1 diabetic since childhood.** Uses Dexcom CGM for real-time blood sugar monitoring 24/7, shares data with doctors. Describes it as “a game changer.” [04:07–04:43] — has more health app exposure than most participants due to medical necessity, though this doesn’t necessarily translate to broader technical sophistication.
- Does NOT log meals or nutrition in any current app. [04:50]
- Apple Health complaint: step tracking accuracy drops when signal is lost. [05:39]

#### T1: Home Screen Exploration (07:46–13:41) | SEQ: 6

- **First thing noticed:** Wellness score, “because it’s at the top and it’s kind of big.” [07:56] — visual prominence drives attention.
- Immediately noticed injection day reminder and the + button. Expressed uncertainty: “I’m kind of like, do I tap there [log injection label] or the plus sign?” [07:56] — noticed both entry points and was confused about which to use.
- After exploring + button: identified injection, side effects, meal, water logging options. “I feel like basically you can like input any of this stuff on here.” [12:09]
- Could articulate purpose: “To help you be as healthy as possible while taking a GLP-1 medication.” [10:44]
- **Key observation:** “If it wasn’t for the option to enter in when you did your injection, I wouldn’t really know per se that this is geared towards people using GLP-1s. I would just think it was a general health and nutrition app.” [12:46] — **she doesn’t see strong GLP-1 differentiation beyond injection logging.** Unique perspective driven by her existing health app experience.

#### T2: Log Medication (13:41–17:45) | SEQ: 7

- **Entry path:** Home card (“injection day, log injection”). Straight path, no detour. [13:56]
- Logged smoothly. “It kind of just guided you right through it. I don’t really know how anyone can mess that up.” [15:13]
- **Confirmation confidence: 5.** “The check mark solidified to me that it went through. But then I’m coming back to this main screen and I kind of wish maybe under injection day it would say like ‘last logged,’ so you know it went through for sure.” [15:35] — **she wants persistent confirmation on the home screen, not just a transient signal. Connects to F1 (toast notifications invisible).**
- Body map: 6/7 usefulness. “Pretty much what I expected.” [16:45] — less surprised than other participants, likely because of her existing Dexcom/medical device experience.
- **Comparison:** “It’s not really hard for me to keep track of it in my head. It’s only something I have to remember once a week. But it can’t hurt to have it tracked.” [17:03] — lowest enthusiasm for injection tracking, because her cognitive load is lower (only 2 months on GLP-1).

#### T3: Log a Meal (17:45–24:42) | SEQ: 7

- **Entry path: + button.** “I think I’d click the plus sign and click meal.” [17:57] — one of only 2 participants (with P01) to use the + button for a task.
- **Input method: Photographed.** “I would definitely take a photo because that makes it easier.” [17:57] — stated intention before seeing options.
- **Expected AI photo recognition:** “I kind of figured with all of AI’s advancements that it would probably allow me to take a photo, and it did.” [20:11] — the only participant who expected this capability based on general AI awareness rather than being surprised by it.
- **Nutritional accuracy:** Yes. Accuracy reasoning was detailed and knowledgeable: “Avocados and chicken are very high in protein… leafy greens are high in fiber… not seeing any processed foods.” [21:32] — evaluating with real nutritional knowledge.
- **Detail level:** Wanted more — “carbohydrates and sugars and specific numbers.” [22:07] — then was shown calorie view and liked the specifics.
- **Display preference: Wanted BOTH combined.** “I like this version better because I like specific numbers. But I honestly wish it would combine the two because the words on the first one were like motivating, like excellent choice, high in fiber. If they could combine the two, that would be amazing.” [22:46] — **the only participant to explicitly request combining the two views rather than choosing one.** Also: “I would prefer not to have to switch back and forth, but I would want both insights.” [23:54]
- **Daily tracking:** Uncertain about consistency. “It depends like how busy I am… sometimes I’d forget to do it.” [24:38] — honest about real-world friction.

#### T4: AI Chat (25:17–33:56) | SEQ: 6

- **Part A — Found AI Coach via wellness score → coach path.** First went to wellness score (“seeing that number overall would give me a good idea of how I’m doing”), then navigated to Coach → “Check my progress.” [25:43–26:34]
- **Engaged with coach for recipes:** “Give me a meal idea” → AI recognized Jennifer’s nausea/fatigue and suggested gentle meals. “That’s cool how it recognized that Jennifer’s having nausea and fatigue, so it suggested meals that are gentle on the stomach.” [28:01] — noticed the personalization.
- Asked how to make a specific meal — AI provided the recipe. [29:29]
- **Would use:** “I really enjoy trying new recipes and experimenting in the kitchen. This is something I already do.” [30:56] — recipe generation is her primary use case.
- Uses ChatGPT for recipes already. [30:01]
- **Reveal — chat logging was confusing.** “Did it actually log? Or did it just log that I’m planning on using my thigh? I don’t know.” [32:40–32:52] — **⚠️ PL1/PL4: The AI response was ambiguous about whether it logged an actual injection or a planned one. The chat language wasn’t clear enough to distinguish action from intent.**
- **Chat vs. UI preference: UI.** “I thought it was just easier to tap on the little body, like where I did it, and then I just pressed log and that was it. Much more simpler.” [33:36] — directness and clarity of the UI logging path.

#### T5: Learning Pathways (33:56–40:34) | SEQ: 7

- **Found Learn directly.** “Maybe if I click learn.” [34:23] — no detour.
- **Content value for newcomers:** “This would be good when you’re just starting. It could be scary at first, implementing a new medication. Being able to click on ‘take a breath,’ like reassuring.” [34:40]
- **Video suggestion:** “Maybe having a video too, because I’m sometimes a more visual learner. If I could see somebody doing their injection, that would make me feel more confident for the first time.” [35:14] — **concrete feature request.**
- **“Chutes and Ladders” critique:** “I kind of feel like I’m playing like Chutes and Ladders or something. Why do they have them with the little squigglies? Couldn’t they just make bullet points or something?” [36:02] — **the most memorable visual design critique in the entire dataset.** She’s questioning the pathway metaphor itself.
- **Would NOT spend time on learning content.** “I don’t really see a point to it.” [39:11] — but for different reasons than P03. P03 already knew the content; P06 doesn’t understand what some sections are trying to accomplish: “Why your why matters — I don’t really understand that. It doesn’t resonate with me.” [40:02] — **the behavioral science framing (ACT, values work) is opaque to her.**
- **Purpose:** “Make you feel more confident and give you knowledge on how everything works and what to expect.” [37:02]

#### T6: Evening Reflection (40:39–44:22) | SEQ: 7

- **Found evening reflection immediately.** “I’d probably come here where it says reflect on your day.” [41:25]
- **Engaged thoughtfully.** Typed real responses: “Exercised for 30 minutes” / “I was feeling fatigued and I took a nap” / “I’m going to try a new dinner recipe.” [41:47–42:05]
- **Appreciated the AI personalization:** “Sounds like you balance your day with great intention, prioritizing both moving and rest. I love that you’re exploring a new recipe.” — “That’s kind of cool.” [42:23]
- **Would use, conditionally:** “Not every day, but if I’m not super tired and end up falling asleep without doing it.” [42:58] — practical constraint.
- **Positive reinforcement is the driver:** “I like that it’s motivating… positive reinforcement always gets me going.” [43:19]
- **Purpose:** “So you can unwind at night and reflect. Remind yourself what went well and what you need to work on. Almost like a self-reflection journal.” [43:54]

#### Backup: Meal Planning (44:22–50:16)

- **Went to AI Coach first for meal planning** (unprompted). Typed “make me a shopping list and meal plan for the next 3 days.” [45:15] — she defaulted to chat because “with AI you can basically do anything.” [47:05]
- AI generated a 3-day plan with shopping list. “That’s kind of cool.” [46:50]
- **Then shown UI version — preferred it.** “I didn’t have to type in a bunch of questions. Just tap the button. I like how it has images of the meals. Breaking down the calories and nutritional facts. And you can just create a shopping list. Much easier.” [48:20] — **another data point for the UI-over-chat preference for structured tasks.**
- **Gentler foods toggle:** Did NOT notice it — but the toggle wasn’t actually visible. **⚠️ Same protocol issue as P04:** the 3-day plan didn’t encompass injection day + 2 days after, so the contextual toggle never surfaced. The facilitator asked about it from header text, not from the functional toggle. P06’s dismissal (“it’s good, but it’s kind of common sense”) was about the concept described in the header, not the actual feature. No discoverability conclusions can be drawn.
- Most useful meal planning features: nutritional facts, photos of meals (“to see if it’s appetizing”). [49:55]

#### Post-Session & Debrief (50:16–56:13)

- **How she’d describe it:** “A good way to keep track of your personal progress. Good way to get recipes and shopping ideas. Helpful to keep track of when and where you did your injection.” [53:28]
- **Frustrated by:** Learning pathways (“Chutes and Ladders”). “I just didn’t really find it engaging.” [54:03–54:20]
- **Genuinely useful features:** Body map injection tracking, wellness score graph. [55:08]
- **Daily use:** Would try to log meals multiple times a day but “sometimes the day gets ahead of you.” [55:45]
- **Would change:** Learning Pathways format. (from facilitator data)
- **Most valuable feature:** “Ability to make healthy meal plans and shopping lists.” (from facilitator data)

#### P06 Key Quotes for Report (with timestamps)

|Timestamp|Quote                                                                                                                                       |Context                                    |
|---------|--------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------|
|07:56    |“The first thing that caught my eye was the wellness score at the top… because it’s at the top and it’s kind of big”                        |Visual hierarchy drives attention          |
|12:46    |“If it wasn’t for the option to enter your injection, I wouldn’t really know this is geared towards GLP-1s”                                 |GLP-1 differentiation concern              |
|15:35    |“I kind of wish under injection day it would say ‘last logged,’ so you know it went through for sure”                                       |Persistent confirmation request            |
|20:11    |“I kind of figured with all of AI’s advancements that it would probably allow me to take a photo, and it did”                               |Expected AI photo recognition              |
|22:46    |“If they could combine the two [views], that would be amazing”                                                                              |Combine calorie + macro views              |
|28:01    |“That’s cool how it recognized that Jennifer’s having nausea and fatigue, so it suggested meals gentle on the stomach”                      |AI personalization noticed                 |
|32:52    |“Did it actually log? Or did it just log that I’m planning on using my thigh? I don’t know”                                                 |Chat logging ambiguity                     |
|35:14    |“Maybe having a video too, because I’m sometimes a more visual learner”                                                                     |Video learning content request             |
|36:02    |“I kind of feel like I’m playing like Chutes and Ladders. Why do they have them with the squigglies? Couldn’t they just make bullet points?”|Learning pathway design critique           |
|40:02    |“‘Why your why matters’ — I don’t really understand that. It doesn’t really resonate with me”                                               |Behavioral science framing opaque          |
|43:19    |“Positive reinforcement always gets me going”                                                                                               |Reflection motivation driver               |
|47:05    |“I just figured with AI you can basically do anything”                                                                                      |AI-first mindset for meal planning         |
|48:20    |“I didn’t have to type in a bunch of questions. Just tap the button”                                                                        |UI preferred over chat for structured tasks|

#### P06 Prototype Limitation Notes

- **PL1/PL4 (chat logging — context window degradation):** By this point in the session, P06 had interacted extensively with the AI Coach (recipes, meal ideas, follow-up questions). The Lovable prototype’s context window had degraded, so when she attempted to log an injection via chat, the AI generated responses that sounded plausible but weren’t actually logging anything. Her confusion (“did it actually log?”) was the correct response — it hadn’t. The AI was essentially hallucinating. This is entirely a prototype limitation and not valid feedback on the chat logging feature or the injection logging language.

#### P06 Analytical Notes

- **The “Chutes and Ladders” comment is a mental model observation, not an actionable design finding.** The pathway format exists because the learning content has branching pathways and embedded reflection exercises that a flat list cannot support. P06 wasn’t familiar with Duolingo-style learning paths (surprisingly, none of the 7 participants appeared to be) and didn’t understand what the visual metaphor was communicating. P02, by contrast, praised the format for exactly the reason it exists (“when you bunch a list together, it scrambles your brain… this one separates it”). The quote is memorable and worth noting in the report as a comprehension observation, but it should NOT drive a design change to the pathway structure.
- **Her “combine the two views” request is unique and actionable.** No other participant asked for a merged view — they all chose one. P06 sees value in both the motivational language (“excellent choice”) and the specific numbers (grams of protein, carbs). A hybrid view that leads with numbers and annotates with encouraging labels might satisfy both preferences.
- **The GLP-1 differentiation observation is worth flagging.** She said the app feels like a general health app unless you notice the injection logging. Given that GLP-1 specificity is a core positioning pillar, this may indicate the home screen needs stronger GLP-1 identity signals — or it may be fine if injection logging is prominent enough to serve as that signal. Worth discussing with the team.
- **Her AI-first approach to meal planning (going to chat before finding the UI version) then flipping to UI preference is the same pattern seen in logging:** AI is the first instinct for open-ended requests, but once a structured UI exists, users prefer it for efficiency. The design implication: AI Coach should be great for discovery and open-ended queries, but every structured task should also have a dedicated UI path.

-----

*P07 summary pending — awaiting transcript upload.*

-----

### P07 — Female, 57, Zepbound (5 months), Calorie default

**Session duration:** 54:13 | **Moderator:** Jack | **Overall tone:** Thoughtful, methodical, honest — lowest self-reported tech comfort but paradoxically the strongest navigator

#### Warm-Up Context (00:00–05:25)

- App comfort: 5/7 — lowest in the cohort. “Because I feel like there’s always some apps that challenge me. Maybe they’re not as intuitive to me.” [03:46]
- Tries new apps regularly.
- Current tools: Apple Health only — for step counting at dance class, once a week. “Other than that, I don’t.” [04:26]
- What she likes about Apple Health: “It’s easy. It tells me exactly what I’m looking for.” [05:08] — simplicity is her primary value.
- No nutrition apps, no medication tracking apps, no AI tools currently in use.
- **The least digitally experienced participant by a significant margin.** This makes her navigation performance all the more striking.

#### T1: Home Screen Exploration (07:42–14:32) | SEQ: 7

- **Immediately decoded the visual language of the app.** Noticed wellness score, interpreted the green ring as “good range, not necessarily great, but a good range. A little bit more than 3/4 of where you should be.” [08:10] — she read the progress ring correctly without any prompting.
- **Identified the category rings as progress indicators:** “It looks like they have rings around them, which I would think they would indicate how much activity I’ve done. That’s at about 50%.” [08:10] — no other participant read the rings this precisely.
- **Hypothesized the wellness score composition:** “I would hope the sleep one is tracking… I’m thinking all those things together come together and give you a wellness score. Could be wrong.” [09:22] — correct hypothesis, articulated unprompted.
- Explored activity, sleep, coach insights, daily check-in. “Yep, exactly as I expected” [09:46] — her predictions were consistently correct.
- **Noticed the Coach button at the bottom:** “I like the fact that there’s a coach button down the bottom.” [10:24] — she saw the bottom nav naturally.
- **Noticed the 7-day wellness trend:** “It gives you a trend for 7 days. That’s also a really nice feature. Because you can see this person kind of hovered and then dipped down.” [11:57] — engaged with the temporal data.
- Could articulate purpose comprehensively: “For someone taking this medication to be able to track their entire wellness. Eating, exercising, sleep… medication regularly. Because those things are all really important on the type of medication I’m on.” [13:14]
- Positive standout: “I like that it’s so easy to use. I like that AI is incorporated into it.” [14:03]

#### T2: Log Medication (14:32–19:10) | SEQ: 7

- **Initially went to meds icon.** “So I would go to the medicine little icon. It comes up, it brings you a calendar.” [14:50] — same meds-screen error as P03, P05. Tried to tap the calendar date and couldn’t log from there.
- **Self-corrected:** “If you go down a little bit further in the screen, just under the AI section, it actually says injection day… there’s a document, it brings up another screen.” [15:44] — found the home card path.
- **Why she went to meds:** “It literally says meds. So I would have expected that if I went there, that would have been an option.” [17:52] — **clearest articulation of the F6 meds screen expectation mismatch.** The syringe icon + “meds” label = expectation of logging functionality.
- “It was very easy once I figured out that you needed to do it from that little section.” [16:37] — the actual logging flow is a 7; the discoverability is the only friction.
- Body map: 7. “It was fun. Very easy.” [18:53]
- Confirmation confidence: 7.

#### T3: Log a Meal (19:10–25:27) | SEQ: 7

- **Input method: Photographed.** “I feel like it’s always easiest.” [21:28]
- Went through photo flow quickly and naturally. AI recognized the salad accurately.
- **Nutritional detail:** Satisfied. “It’s short, it only has a couple of key points, which is what you’re really looking for. Protein is always key.” [21:42]
- **Display preference: Calorie view, strongly.** Immediately identified what the calorie view does better: “The other one literally pointed out how much protein you’ve had. This doesn’t tell me what my caloric intake was for the day.” [22:47] And: “It’s wordier. Not as bold and in your face. Not as direct.” [23:20] — **the most articulate critique of the macro view in the dataset.**
- Calorie view enables meal decision-making: “It told me how many calories I had left for the day… it can prompt you like, what am I going to have for dinner?” [23:46] — she sees it as forward-looking, not just retrospective.
- Toggle: “I’d pick one and stick with it, and I would pick the other one [calorie]. I’m being honest.” [24:24]
- **Daily tracking — practical constraint:** “I would probably want the option to add it in at a later time. I’m often out at a business lunch. It’s not something you’re going to want to do at a business lunch.” [24:57] — **unique real-world constraint: professional context prevents real-time logging.**

#### T4: AI Chat (25:32–34:42) | SEQ: 5

- **Part A — Went to Progress first.** Found the 7-day progress summary via the progress arrow. [26:22] — navigated to a valid summary view but not via AI Coach.
- **Facilitator guided her to AI Coach.** [27:30]
- **Tried microphone first — non-functional.** **⚠️ PL2.** [27:38–27:52]
- **Typed:** “How many calories do I have left?” [28:11] — practical, forward-looking query tied to her meal decision-making mental model.
- **AI didn’t directly answer** the calorie question but gave meal suggestions instead. “It’s not necessarily giving me how many calories, but it is telling me about what I should have for another meal.” [28:31] — **⚠️ PL4: AI response missed the specific query.**
- Liked the follow-up questions the AI asked: “How are you feeling after your lunch? Was I satisfied? Was I still hungry?” [28:54]
- **SEQ: 5.** Explicitly because of the microphone: “Because I would prefer that the microphone worked right the first time.” [29:32–29:38] — **⚠️ PL2 directly caused the score reduction.** Without it, likely 6-7.
- “I’m getting very used to just chatting with my phone, which is kind of crazy, but I feel like that’s where everything’s going.” [29:47] — she sees voice-first AI interaction as the future direction, even though she doesn’t currently use AI.
- **AI Coach value:** “It’s focused on this app and what I’m going through. I don’t have to tell it that I’m taking a GLP-1 and looking for nutritional values. It already knows.” [30:04] — **contextual AI advantage over generic tools, articulated clearly.**
- **Reveal — chat logging:** Logged injection via chat. Preferred UI: “The actual box on the app went away after I logged it. Visually telling me you’ve logged that. This one has a check mark but that one visually went away.” [32:29] — **completion state feedback is the reason she prefers UI logging.** She needs the visual confirmation, which the home card disappearance provides but chat does not.
- **Chat vs. UI:** “It just feels like it’s easier to just log it myself than go into a chatbot.” [34:16]

#### T5: Learning Pathways (34:42–40:34) | SEQ: 7

- **Found Learn immediately.** “It has a learn button right here at the bottom.” [35:01] — **the only participant to describe the Learn button’s location as obvious.** This despite being the lowest self-rated tech comfort participant. The paradox deepens.
- Explored content enthusiastically: getting started, side effects, eating with medication. “There’s a lot of really easy, basic things, and then you click on them and they give you even more information.” [35:42]
- Liked the progressive disclosure: “The links take me to the next place and it takes me to the next place if I have questions. Absolutely really like that.” [35:42]
- **Purpose:** “Educate people as to what things you should be looking at, how you should be taking your medication. And it looks like there’s a way to personalize your own journey.” [36:39]
- **Would use, but sees AI as alternative:** “It would be a toss-up between going here and asking some of these same questions to the chatbot.” [39:50] — but: “I feel like it gives people options if you’re not an AI type person, which I’m typically not.” [40:19] — **she positions Learn as the non-AI path to the same information. This is a valid segmentation insight.**

#### T6: Evening Reflection (40:41–47:07) | SEQ: 7

- **Found evening wind-down immediately.** “The very first thing it gives you is like your evening wind-down. I’m guessing if I hit the reflect button it’s going to give me some information.” [41:52]
- **Engaged thoughtfully.** Liked the question format: “I like the fact that it’s asking me questions, which is nice.” [43:16] And: “It prompted me, asked a couple questions. And then it’s giving me some words of encouragement, which is always really nice at the end of your day.” [44:00]
- **Felt natural.** [44:17]
- **Would have written more with voice input:** “I probably would have commented more or said more had the microphone worked.” [44:17] — **⚠️ PL2 limiting expression depth. Confirms voice input demand.**
- **Would use, especially with prompts:** “I would more likely do it if it prompted me at the end of the day. If I could set a timer or every night, you know, my phone tells me it’s time to go to bed. So if it prompted me, I would be more apt to do it more regularly.” [45:46] — **THE key adoption insight for reflections. Push notifications / bedtime prompts as the driver. She already has a phone-before-bed habit; reflections need to hook into it.**
- Also: “I feel like I’m a type of person who would do it. But I feel like I would make sure that I did it if it prompted me.” [45:46] — willingness exists but needs a system nudge.
- **Purpose:** “You always want to reflect on how— on your positive and negative things that happen during the day.” [46:32] — she already does this at work.

#### Post-Session & Debrief (47:07–54:12)

- **How she’d describe it:** “A great way to track what you’re doing and to make sure you’re keeping on target. Pretty easy to use.” [49:34]
- **Most engaged:** “Just getting in there and learning about the app. Having lots of things on the first screen is really important.” [50:14]
- **Navigation pain point she avoids:** “I’m the kind of person who X’s out of things by mistake because I can’t figure out how to get back. And then you can’t find it.” [50:34] — **this self-awareness about navigation challenges makes her successful navigation of this app even more notable.**
- **Not frustrated** at any point. [50:57]
- **Daily routine fit:** “I am on a weight loss journey, so I feel like it’s important to do the things that are on this app.” [52:09]
- **Positioning recommendation:** “It would be great if the advertising could be geared towards tracking your journey, because this is not something you’re just gonna lose weight on. You have to modify your life and track and be on a journey.” [52:52] — **unsolicited positioning/marketing feedback. She’s articulating the app’s value proposition better than most marketing copy could.**
- Final thought: “It’s easy to take the medication and lose weight, but you have to change your lifestyle.” [53:48]

#### P07 Key Quotes for Report (with timestamps)

|Timestamp|Quote                                                                                                                                                 |Context                                                    |
|---------|------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
|03:46    |“There’s always some apps that challenge me. Maybe they’re not as intuitive to me”                                                                    |Self-assessed low tech comfort                             |
|08:10    |“There’s a green line around it, so it looks like you’re in a good range, not necessarily great, but a good range”                                    |Decoded wellness score ring unprompted                     |
|09:46    |“Yep, exactly as I expected”                                                                                                                          |Predictions consistently correct throughout                |
|10:24    |“I like the fact that there’s a coach button down the bottom”                                                                                         |Noticed bottom nav naturally                               |
|11:57    |“It gives you a trend for 7 days. That’s also a really nice feature”                                                                                  |Temporal data engagement                                   |
|14:03    |“I like that AI is incorporated… you don’t have to go somewhere else to ask a question”                                                               |Contextual AI value                                        |
|17:52    |“It literally says meds. So I would have expected that if I went there, that would have been an option”                                               |F6 meds screen expectation mismatch — clearest articulation|
|21:42    |“It’s short, it only has a couple of key points, which is what you’re really looking for. Protein is always key”                                      |Nutritional detail satisfaction                            |
|23:46    |“It told me how many calories I had left for the day… it can prompt you like, what am I going to have for dinner?”                                    |Calorie view enables forward meal planning                 |
|28:11    |“How many calories do I have left?”                                                                                                                   |Natural, practical AI query                                |
|29:47    |“I’m getting very used to just chatting with my phone, which is kind of crazy, but I feel like that’s where everything’s going”                       |Voice-first AI future                                      |
|30:04    |“It’s focused on this app and what I’m going through. I don’t have to tell it that I’m taking a GLP-1”                                                |Contextual AI advantage                                    |
|32:29    |“The actual box on the app went away after I logged it. Visually telling me you’ve logged that”                                                       |UI completion feedback preferred                           |
|36:39    |“It looks like there’s a way you can even personalize your own journey here”                                                                          |Learning path personalization noticed                      |
|40:19    |“It gives people options if you’re not an AI type person, which I’m typically not”                                                                    |Learn as non-AI path to information                        |
|45:46    |“I would more likely do it if it prompted me at the end of the day”                                                                                   |Push notification as reflection adoption driver            |
|50:34    |“I’m the kind of person who X’s out of things by mistake because I can’t figure out how to get back”                                                  |Self-aware navigation challenge                            |
|52:52    |“The advertising should be geared towards tracking your journey. This is not something you’re just gonna lose weight on. You have to modify your life”|Positioning recommendation                                 |
|53:48    |“It’s easy to take the medication and lose weight, but you have to change your lifestyle”                                                             |App value proposition articulated                          |

#### P07 Prototype Limitation Notes

- **PL2 (microphone):** Tried to use mic in AI Coach. Non-functional. Directly caused her T4 SEQ of 5 — she explicitly stated this. Also limited her reflection input depth (“I probably would have commented more had the microphone worked”).
- **PL4 (AI response quality):** When she typed “how many calories do I have left?” the AI gave meal suggestions rather than answering the specific calorie question. Minor but notable — the query was clear and the AI missed it.

#### P07 Analytical Notes

- **The P07 paradox is one of the strongest findings in the dataset.** The participant who rated herself lowest on tech comfort (5/7), who only uses Apple Health once a week at dance class, who describes herself as someone who “X’s out of things by mistake” — was the best navigator of all 7 participants. She found Learn immediately (“right here at the bottom”), she found reflections immediately, she decoded the wellness score rings unprompted, she correctly hypothesized the score composition, and she consistently predicted what features would do before tapping them. This tells you the app’s information architecture is fundamentally sound. The navigation problems other participants experienced are styling/visibility issues (F1), not structural ones. If the least confident user can navigate it, the architecture works.
- **Her reflection adoption insight is actionable.** “If it prompted me at the end of the day” — she has an existing phone-before-bed habit, and she would do reflections if they hooked into that routine via a push notification. This is the most concrete adoption mechanism suggested by any participant. Combined with P04’s gratitude journal habit and P05’s “if it made me feel good, I would probably continue,” the reflection adoption strategy writes itself: prompt users at bedtime, provide immediate positive feedback, and let the habit self-reinforce.
- **Her positioning feedback is strategic gold.** “Weight loss is more than taking medicine. You have to change your lifestyle.” She’s articulating the app’s value proposition — and she’s saying the marketing should lead with the journey/transformation framing, not the medication management framing. This aligns with the behavioral science foundation of the app.
- **Her T4 SEQ of 5 is entirely PL2.** She said so explicitly. Remove the microphone issue and her score would likely be 6-7. This should be footnoted in the report.

-----

*All 7 participant transcript summaries complete.*

-----

## PHASE 3: CROSS-PARTICIPANT SYNTHESIS

### Executive Summary

The GLP-1 support app validated strongly across all 7 participants. Overall post-session satisfaction averaged 6.6/7, with every participant expressing willingness to use the app and two (P03, P04) stating they would replace their current health apps with it. The app’s core value proposition — consolidating medication tracking, nutrition logging, AI-powered coaching, behavioral learning, and reflective journaling into a single GLP-1-specific experience — resonated universally.

The primary usability gap is visual, not structural. The app’s information architecture is sound (validated by P07, the least tech-comfortable participant, who navigated every feature intuitively), but interactive elements blend into the visual design, causing discoverability failures for the bottom nav, the + button, toast notifications, and some card CTAs. This is a styling problem with a clear remediation path, not an architectural redesign.

Three features generated consistent delight: photo-based meal logging (6/7 chose it unprompted), the body map injection site tracker (7/7, mean 6.7/7 usefulness), and the AI Coach once discovered (7/7 found it useful, not a novelty). The AI Coach’s main challenge is discoverability and labeling — only 2-3/7 found it independently for a directed task.

-----

### I. DESIGN FINDINGS (Actionable)

#### F1: Interactive elements lack visual differentiation — the app’s primary usability issue

**Severity: High | Frequency: 7/7 affected in some way**

The app’s visual cohesion creates a consistent aesthetic that participants praised, but it comes at the cost of affordance clarity. Functional interactive elements are styled too similarly to informational and decorative elements, causing a cascade of discoverability failures across the UI.

**Manifestations:**

|Element                   |Issue                                                     |Affected                                                                     |Evidence                                                                                   |
|--------------------------|----------------------------------------------------------|-----------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
|Bottom nav bar            |Not registered as navigation                              |3/7 didn’t notice tab bar; P05 couldn’t relocate Learn despite having used it|P05 [49:25]: “I just didn’t even think to look along the bottom”                           |
|+ button                  |Overlooked as primary action entry                        |5/7 never noticed it; only P01 used it for a task                            |P01 [18:22] was the exception: “It’s kind of self-explanatory because it has the plus sign”|
|Toast notifications       |Not noticed as completion confirmation                    |Multiple participants uncertain whether logging completed                    |P04 [15:22]: “I did not know it was done until I knew it was done”                         |
|Card icon vs. button (F11)|Decorative icon mistaken for CTA; actual button below fold|P04 directly affected                                                        |P04 [14:03]: “Oh, I hit the wrong thing here… Wrong button”                                |
|Evening reflection card   |Missed on home screen                                     |2/7 (P01, P02) didn’t find it                                                |P02 [45:35]: “Maybe it’s the way it looks all together”                                    |

**Strongest evidence — P05 recognition-vs-recall failure:** P05 found and interacted with the Learn tab during T1 exploration [11:41], but during directed T5 task could not relocate it. The facilitator asked about learning/education five times before P05 finally noticed: “Oh wait, hold on. Learn. Okay. Duh.” [47:45]. Her explanation: “I kept keying on the home key… I just didn’t even think to look along the bottom to see that there was a learning section.” [49:25]

**Narrative framing — P01’s Apple Health complaint:** P01 described her frustration with Apple Health’s interface during warm-up: “It all just blurs together, like blends, it doesn’t really stick out.” [06:52] — the exact same problem the prototype has, described by the participant before she ever encountered it in the test app.

**Architecture validation — P07 paradox:** The participant who self-rated lowest on tech comfort (5/7) navigated every feature on her first attempt, found Learn “right here at the bottom” [35:01], decoded the wellness score rings unprompted, and consistently predicted feature behavior before tapping. If the least confident user can navigate the app, the information architecture is sound. The problems are styling-level, not structural.

**Toast notification sub-finding (F1a):** Participants relied on three alternative completion cues instead of toasts: (1) home screen card disappearing (P02, P03, P07), (2) in-flow confirmation/review screen (P01), or (3) remained uncertain (P04, P06). P06 specifically requested a persistent “last logged” indicator on the home screen [15:35]. **Two-part recommendation: (1) Restyle toast notifications so they are visually distinct and noticeable — the current styling blends into the UI the same way the bottom nav does, making them effectively invisible. (2) Add persistent state indicators on the home screen (e.g., “last logged: today”) and ensure structural UI changes (card removal, state update) serve as a reinforcing completion signal alongside the toast.**

**Hesitation taxonomy (from Dovetail):** The three triggers for navigation hesitations were: bottom-nav icon ambiguity, content positioned below the fold, and unexpected locations for core features.

-----

#### F6: Meds screen should support logging — users’ instinct reveals a primary entry point

**Severity: Medium | Frequency: 3/7 (P03, P05, P07)**

Three participants initially navigated to the meds section (the syringe icon under the wellness score) when asked to log an injection. Rather than a “mismatch,” this reveals a natural entry point that should be supported. The meds view currently shows informational content only (scheduled dates, dosage, injection site history), but users repeatedly tapped on the historical calendar — specifically the “today” date — expecting to log from there.

|Participant|What happened                                              |Quote                                                                                                           |
|-----------|-----------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|P03        |Went to meds, tried tapping calendar, couldn’t find logging|[13:19]: “I would assume I would hit this meds button… I don’t see a spot to say you’re doing it”               |
|P05        |Went to meds, saw schedule/dosage info but no logging      |[18:40]: “Pressing on the schedule does not give you the today’s information”                                   |
|P07        |Went to meds, tried to tap calendar date                   |[17:52]: “It literally says meds. So I would have expected that if I went there, that would have been an option”|

All three self-corrected by finding the home screen injection card. P03 gave a 4 on this task, self-attributing the error. P07 articulated the root cause most clearly: the syringe icon + “meds” label creates an expectation of logging functionality.

**Design opportunity:** The meds view SHOULD allow logging from within the view, and the calendar’s “today” date should be tappable to initiate the injection logging flow. Users going there first means it may be a primary method for logging — the instinct is correct, the UI just doesn’t support it yet. This is a refinement, not a redesign.

**Note:** P03’s learning transfer is notable — after her T2 meds-screen error, she explicitly avoided the same pattern in T3: “Well I learned not to hit those.” [18:03]. This suggests a fast learning curve even when initial discoverability is imperfect.

-----

#### F9: Users need temporal navigation for progress — daily, 7-day, 30-day views + date-specific calendar

**Severity: Medium | Frequency: 3/7 explicitly sought this; broader pattern across T4**

When asked to find a summary of their week, 3 participants independently sought a fast, non-AI path to progress data. The current progress icon (small up-trend arrow on home screen) was not intuitive, and users expected a more prominent, structured progress view.

|Participant|What they expected                          |Quote                                                                                                           |
|-----------|--------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|P01        |Calendar icon                               |[35:37]: “I was looking for like a calendar”                                                                    |
|P03        |Homepage button for weekly summary          |[29:44]: “I would love if there was just a button on the front… It’s quicker. You don’t have to type a question”|
|P04        |Wellness score to function as weekly summary|[22:35]: “I would assume it’s in that wellness score… how well you’re doing on a daily basis, maybe weekly”     |

**Design questions this surfaces:**

- Should users toggle between daily, 7-day, and 30-day summary trend views?
- Should there be a calendar interface for date-specific lookback (“what happened last Tuesday?”)?
- How prominent should temporal navigation be in the UI?

**Supporting use cases from participants:** P01 described needing historical data for doctor visits [21:30]; P04 connected it to emotional eating pattern recognition [38:23]; P07’s calorie view enabled forward meal planning [23:46].

**Note:** The catch-up logging feature in the production app (morning recap of yesterday’s unlogged items, evening quick-log before reflection) partially addresses the temporal navigation need by ensuring data completeness, but the viewing/browsing of historical data remains a design gap.

-----

#### F11: Card icon/button affordance confusion on meal logging

**Severity: Low-Medium | Frequency: 1/7 directly affected (P04), but represents a broader pattern**

On the meal logging card, a decorative icon above the fold was mistaken for the tappable button, while the actual CTA sat below the fold. P04 tapped the icon, got confused, then found the real button: “Oh, I hit the wrong thing here. So I went to nutrition and then hit log a meal, log a meal, but it’s not— oh, there it is. Wrong button.” [14:03]

This is not a prototype limitation — it’s a real UI issue. The icon needs to either be made tappable, visually distinguished from the button, or the actual CTA needs to be above the fold.

-----

### II. FEATURE VALIDATIONS (What Worked)

#### F3: Photo-based meal logging is a breakout feature

**Strength: Very High | Frequency: 6/7 chose photo unprompted**

Six of seven participants chose to photograph the meal image without being prompted or told about the feature. Multiple participants expressed genuine surprise and delight at the AI’s ability to recognize and analyze the meal from a photo.

|Participant|Key moment                                                                                                                              |
|-----------|----------------------------------------------------------------------------------------------------------------------------------------|
|P02        |“I didn’t think it was gonna pick up the whole meal the way it did, so that was pretty cool” [20:38]                                    |
|P03        |Chose photo as “easiest,” prioritized accuracy enough to backtrack when Panera attribution was wrong                                    |
|P04        |“If I could take a picture of it, I would do it all the time” [20:23]; “It would be a pain in the butt” to type [20:33]                 |
|P05        |“That’s really cool, actually” [24:26] — genuine delight                                                                                |
|P06        |Expected AI photo recognition: “I kind of figured with all of AI’s advancements that it would probably allow me to take a photo” [20:11]|
|P07        |“I feel like it’s always easiest” [21:28]                                                                                               |

**P01 outlier:** The only participant who typed a meal description instead. Her reason was AI fluency (“I use a lot of AI tools daily”), not because the photo option was unclear. [25:34]

**Adoption gatekeeper:** P04 explicitly tied daily tracking adoption to the photo feature: if she can photograph, she’ll track every meal; if she has to type, she won’t. This makes photo logging a make-or-break feature for sustained daily engagement.

-----

#### F4: Body map injection site tracker is universally loved

**Strength: Very High | Frequency: 7/7 found it, 7/7 rated it highly (mean 6.7/7 usefulness)**

Every participant found the body map, and every participant rated it positively. Multiple participants called it out as better than their current tracking method and identified injection site rotation as a real pain point the feature addresses.

|Participant|Quote                                                                                                             |
|-----------|------------------------------------------------------------------------------------------------------------------|
|P01        |“It was better than expected… typically it would just be like, yes, today, right arm” [20:07]                     |
|P02        |“This is a lot better because the app that I use, I think it only tracks my infusions” [15:46]                    |
|P02        |“I didn’t expect to have like prior injection sites… which is good” [15:19]                                       |
|P03        |“It was easier… She had that nice little map. And it kept track of where you had previously injected” [16:57]     |
|P05        |“I like that it tells you where your last one was because in [my app] I actually have to go back and look” [22:21]|

**What makes it work:** The combination of visual selection (tap on body), historical context (where you injected last time), and rotation reminders. No competitor app in participants’ experience provides all three.

-----

#### F2: AI Coach is valuable once found — the discoverability problem is real but solvable

**Strength: High (post-discovery) | Discoverability: 2-3/7 found independently for T4 task**

Every participant who used the AI Coach found it useful and said they would use it (not a novelty). But only 2-3 out of 7 navigated to it independently when asked to find a weekly summary/progress view.

**Discoverability breakdown:**

|Path taken in T4 Part A|Participants                                                     |
|-----------------------|-----------------------------------------------------------------|
|Found AI Coach directly|P02, P03 (2/7 clear; P06 went to wellness score first then coach)|
|Went to Progress first |P01, P05, P07 (3/7)                                              |
|Went to Wellness Score |P04, P06 (2/7)                                                   |
|Needed guided bridge   |P01, P04, P05, P07 (4/7)                                         |

**Root causes of discoverability gap:**

1. **Labeling:** “Coach” is ambiguous. P04 [09:44]: “Is it a tutorial? Is it a more descriptive part of the app? Is it something giving you pep? Pumping you up?” P02 [31:49]: “At first I thought it was like a customer service type thing.”
1. **Mental model:** Users don’t instinctively think of AI for summary/progress tasks. P03 [30:09]: “It’s quicker. You don’t have to type a question” — she wanted a button, not a conversation.
1. **AI literacy:** P04 [25:45]: “I have to get used to using AI, which I’ve just started using in the past couple of months. The notion of using AI is intimidating.” P05 [36:49]: “I’m not used to all of the things that are the potential that there is.”

**Post-discovery value — what participants used it for:**

- Progress summaries and weekly check-ins
- Recipe and meal ideas (P06’s primary use case)
- Health questions (“Is there a certain time of day you should take an injection?” — P01)
- Motivational feedback and accountability (P05: “It’s almost like having a buddy”)
- Side effect management tips (P04: “ideas to help with the nausea, which is actually pretty good”)

**Chat vs. UI preference — nuanced, not binary:**

- 6/7 preferred UI screens for structured logging tasks (injections, meals)
- But participants valued the AI Coach for different things than the UI provides:
  - P04 [28:48]: “The screens feel more natural, but I like the idea of talking to the coach because I like the feedback”
  - P05 articulated a temporal model [42:29]: chat for onboarding (“the first few times”), UI for maintenance (“once you’re in the rhythm”)
  - P07 [30:04]: “It’s focused on this app and what I’m going through. I don’t have to tell it that I’m taking a GLP-1”
- **Design principle:** AI Coach is for exploration, questions, and coaching feedback. UI is for repetitive, structured actions. Both paths should exist for every task, but each serves a different need.

**⚠️ PL1 note:** Chat-based logging was validated in the MVP and will be fully functional in production. Any participant preference for UI over chat for logging may be partially influenced by prototype inconsistency (chat logging worked for P03, P04; failed for P02; hallucinated for P06). This is a general context note, not a finding.

-----

#### F5: Nutritional display — show both views by default, with option to hide calories

**Strength: High | Frequency: 6/7 preferred calorie view; 1/7 explicitly requested combined view**

Regardless of which view participants started on (alternating calorie/macro across sessions), 6 of 7 preferred the calorie tracking view. However, the framing of this as a binary choice between two modes may be the wrong lens. P06 identified the real opportunity: participants want BOTH the specific numbers (calories, grams of protein) AND the high-level nutrient quality descriptors (whole vs. mixed vs. processed, “excellent choice,” “high in protein”).

|Participant|Started on|Preferred       |Reasoning                                                                                                |
|-----------|----------|----------------|---------------------------------------------------------------------------------------------------------|
|P01        |Calorie   |Calorie         |Macro view “more confusing… I don’t know what they’re talking about with the mixed and the whole” [27:42]|
|P02        |Macro     |Calorie         |Preferred the picture and calorie numbers [23:39]                                                        |
|P03        |Calorie   |Calorie         |“There would be very little processed foods anyway with me. We worry about the calories” [23:36]         |
|P04        |Macro     |Calorie         |“I like that much better. It tells you how many carbs, how many grams of protein” [19:37]                |
|P05        |Calorie   |Ambivalent/Macro|Only participant to waver — tracks protein, not calories [31:10]                                         |
|P06        |Macro     |Both combined   |“If they could combine the two, that would be amazing” [22:46]                                           |
|P07        |Calorie   |Calorie         |“Not as direct” about macro view; calorie view enables meal decision-making [23:46]                      |

**Design opportunity:** Rather than two mutually exclusive modes, show both by default — the calorie/macro numbers alongside the qualitative nutrient descriptions. The “mode” becomes less about choosing one view over the other and more about choosing to HIDE calories (for users who find calorie counting counterproductive or triggering). This respects the 6/7 who want numbers while preserving the motivational language P06 valued, and creates a healthier default for users who prefer not to see calorie counts.

**Toggle preference:** 5/7 would pick one view and stick with it — but if both views are combined by default, the toggle becomes unnecessary for most users.

-----

### III. NUANCED / SEGMENT FINDINGS

#### F7: Learning pathways — content valued, most useful for newer users, discoverability is the real issue

**Content:** 7/7 understood the pathway structure. 7/7 engaged with content once found. The information was valued as a reference, particularly by those earlier in their medication journey.

**Engagement level:** Moderate. Most participants said they would go through the content once but not return regularly. P03 [36:49]: “It took me a long time to navigate to where I currently am… I don’t know that I would have much need for any of this.” But for newer users: “For somebody who is new, absolutely.” [37:13]. P05 would go through “at least once” [53:15]. P07 saw it as an alternative to AI for the same information [39:50].

**Format:** P02 praised the pathway structure: “When you bunch a list together, kind of like scrambles your brain… this one separates it so it’s like individualized” [38:13]. P06 was unfamiliar with the Duolingo-style format (“Chutes and Ladders”) — this is a mental model observation reflecting unfamiliarity with an established learning UX pattern, not an actionable design finding.

**Discoverability is the real issue:** 5/7 found Learn when directed (P01 detoured through meds first, self-corrected). P04 needed facilitator guidance. P05 failed entirely without five facilitator prompts. The content works — the container (bottom nav tab) is invisible. This is part of F1, not a separate Learn-specific problem.

**Navigation within Learn:** P04 had difficulty navigating back out of a lesson [32:56]: “I just couldn’t figure out how to get back out of it.” She discovered she needed to scroll further down. Minor but worth noting for the pilot.

-----

#### F8: Evening reflections — polarizing feature with high ceiling and specific adoption drivers

**Discoverability:** 5/7 found the evening reflection card on the home screen. P01 and P02 did not find it initially (P01 went to Progress; P02 went to AI Coach and typed “journal”).

**Engagement spectrum:**

|Level               |Participants |Pattern                                                                                                                                                                               |
|--------------------|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|Strong adoption     |P04          |Existing gratitude journaler. “I would absolutely keep it like this. All in one place.” [37:44] Would replace handwritten journal.                                                    |
|Conditional adoption|P05, P06, P07|Would use if prompted/habituated. P07 [45:46]: “I would more likely do it if it prompted me at the end of the day.” P05 [57:17]: “If it made me feel good, I would probably continue.”|
|Minimal engagement  |P03          |Typed “yes” for every prompt. “Natural to ask the questions. Whether I would have an answer, I don’t know.” [41:18]                                                                   |
|Partial engagement  |P02          |Used AI Coach for journaling instead. Found reflection card valuable once shown.                                                                                                      |
|Refused             |P01          |“I hate this.” [51:46] “It’s not rewarding for me.” [52:39] Would rather talk to a human.                                                                                             |

**Key insight — P01’s rejection doesn’t damage overall app perception:** Immediately after refusing reflections, she said “I actually like [the app] though” [53:01]. Reflections are a segment feature, not a universal one. Her rejection was personal and emotional, not a UI problem.

**Adoption strategy (from participant data):**

1. **Push notification at bedtime** (P07): hook into existing phone-before-bed habits
1. **Immediate positive feedback** (P05, P06): the AI’s personalized response to reflection inputs was noticed and appreciated
1. **Consolidation** (P04): having journaling in the same app as everything else removes friction vs. a separate journal
1. **The production app’s catch-up logging feature** — built into the evening reflection — adds practical utility (log forgotten meals) alongside the emotional/behavioral reflection

-----

#### AI Coach labeling and mental model — a solvable positioning problem

Participants’ initial mental models of “Coach” varied widely and affected discoverability:

- P02: “Customer service type thing” [31:49]
- P04: “Is it a tutorial? Is it pumping you up?” [09:44]
- P05: “Almost like having a buddy” [36:49] — discovered after use, not from the label
- P07: Appreciated that “it’s focused on this app… I don’t have to tell it anything” [30:04]

The label “Coach” doesn’t communicate what the feature does. Once participants used it, they understood and valued it — but the label created a barrier to first interaction. This is worth monitoring in the pilot but may resolve naturally as users build familiarity with the app over multi-day use (vs. a single test session).

-----

### IV. TARGET DEMOGRAPHIC VALIDATION

**Business target: Women aged 50-65.**

P07 (57F) and P05 (61F) are squarely in this range and provide the strongest validation of the app’s accessibility for the target demographic:

- **P07** rated herself 5/7 on tech comfort but navigated every feature intuitively, found Learn and reflections immediately, decoded the wellness score unprompted, and articulated the app’s value proposition better than most marketing copy: “Weight loss is more than taking medicine. You have to change your lifestyle.” [53:48]
- **P05** was the most talkative, engaged extensively with every feature, emotionally connected with the AI Coach as a “buddy” for her solo weight loss journey, and asked about pricing (an unsolicited purchase intent signal).

The concern that the target demographic might not be tech-savvy enough for an AI-powered app is directly contradicted by the data. Both target-age participants engaged deeply with AI features and expressed clear intent to use the app daily.

-----

### IV-B. BACKUP TASK: MEAL PLANNING (P04, P06 only)

Only 2 of 7 sessions had time to reach the backup meal planning task. Sample size is too small for frequency-based findings, but the qualitative signal is strong enough to note.

**Meal planning UI vs. AI Coach — same pattern as logging:**
P06 went to AI Coach first for meal planning (“make me a shopping list and meal plan for the next 3 days”), got a functional result, then was shown the UI version and preferred it: “I didn’t have to type in a bunch of questions. Just tap the button.” [48:20]. This mirrors the logging pattern: AI for open-ended exploration, UI for structured execution. P04 found the UI path directly (Nutrition → Plan → Generate).

**Planning horizon insight:**
P04 chose 3 days: “I feel like if I plan too far in advance, I don’t actually do what I set myself out to do.” [45:11] — practical constraint that informs default planning window.

**Shopping list is a standout:**
P04: “The shopping list… It would tell me exactly what I need to buy, and I don’t have to write it out myself. Copy it, paste it into the Giant app, and I’m good to go.” [43:53–44:11]

**Gentle foods — concept resonates, but toggle was not testable:**
⚠️ **Protocol limitation:** The gentle foods toggle is contextual — it only appears when the meal planning window includes injection day + 2 days after. Both participants selected 3-day plans, and the persona’s injection timing meant the 3-day window fell outside the injection day window. The toggle never actually surfaced in the UI. The facilitator asked about gentle foods from header label text, not the functional toggle. **No discoverability or usability conclusions can be drawn from the gentle foods toggle.**

However, the concept resonated strongly with P04, who experiences nausea: “I am one who gets nauseous on this injection, so I would love something that would give me ideas of gentle foods.” [43:31]. P06 dismissed the concept as “common sense” when described [49:31]. The feature’s value appears tied to whether the user personally experiences GI side effects — which is common enough in the GLP-1 population to warrant prominence.

**Meal planning in future testing:** If the diary study or pilot includes meal planning evaluation, ensure the testing window encompasses injection day so the gentle foods toggle is actually visible.

-----

### V. PARTICIPANT SUGGESTIONS & FEATURE REQUESTS

|Suggestion                                       |Source                                                                              |Status                                                                                                      |
|-------------------------------------------------|------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
|Saved/favorited meals for quick re-logging       |P03 [24:40] (WW feature she missed)                                                 |Design consideration for pilot                                                                              |
|Barcode scanning for packaged food               |P04 [03:37] (MFP feature she missed)                                                |Design consideration                                                                                        |
|Meal backdating (log after the fact)             |End-of-day team synthesis; P07 business lunch scenario [24:57]                      |**Partially addressed** by catch-up logging in production. Photo constraint remains for retroactive entries.|
|Progress as calendar with date navigation        |P01 [35:37], P03 [29:44], end-of-day synthesis                                      |Part of F9 design question                                                                                  |
|Video content in Learn pathways                  |P06 [35:14]: “Maybe having a video too, because I’m sometimes a more visual learner”|Design consideration                                                                                        |
|Bedtime push notification for reflections        |P07 [45:46]: “If it prompted me at the end of the day”                              |Adoption mechanism for F8                                                                                   |
|“Last logged” persistent indicator on home screen|P06 [15:35]                                                                         |Part of F1a recommendation                                                                                  |
|Combined calorie + macro nutritional view        |P06 [22:46]: “If they could combine the two, that would be amazing”                 |Design consideration                                                                                        |
|Wearable device integration for sleep data       |P05 [13:29], multiple participants assumed watch integration                        |Design consideration                                                                                        |
|Weight from smart scale integration              |P01 [21:02]: fiancé uses a scale app                                                |Design consideration                                                                                        |

-----

### VI. PROTOTYPE LIMITATIONS — IMPACT ON FINDINGS

|PL#|Limitation                       |Impact on findings                                                                                                                                                                                        |
|---|---------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|PL1|Chat logging inconsistent        |**General note only.** Validated in MVP, will be in production. Chat logging worked for P03, P04; failed for P02; hallucinated for P06 (context window degradation). Excluded from design recommendations.|
|PL2|Microphone non-functional        |P05 and P07 tried it. P07’s T4 SEQ of 5 is entirely attributable to PL2 (she said so explicitly). Confirms real demand for voice input.                                                                   |
|PL3|Dose customization not functional|P01 and P04 tried to change dose. Expected behavior that prototype couldn’t support with fixed persona data.                                                                                              |
|PL4|AI response variability          |Live Lovable AI produced inconsistent responses. May explain some T4 SEQ variability (range 4-7). P07’s calorie question got meal suggestions instead of a number.                                        |

**Net effect on T4 SEQ:** The T4 mean of 5.4 (at benchmark) is likely deflated by PL2 (P07’s score) and PL4 (variable response quality). The real usability gap on T4 is discoverability and AI literacy, not the interaction quality once participants found and used the Coach.

-----

### VII. FINDINGS PRIORITY MATRIX

|Priority       |Finding                                        |Type               |Action                                                                                                                                                            |
|---------------|-----------------------------------------------|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|**HIGH**       |F1: Visual differentiation / affordance clarity|Design             |Restyle bottom nav, + button, toast notifications. Add persistent state indicators. Ensure CTAs are above fold and visually distinct from decorative elements.    |
|**HIGH**       |F3: Photo meal logging (validation)            |Validation         |Protect and polish. This is the breakout feature.                                                                                                                 |
|**HIGH**       |F4: Body map injection tracking (validation)   |Validation         |Protect. Universal love, strong differentiator.                                                                                                                   |
|**HIGH**       |F2: AI Coach value + discoverability           |Design + Validation|The feature works; the label and entry point need refinement. Consider renaming, increasing prominence, or adding contextual prompts.                             |
|**MEDIUM**     |F9: Temporal navigation / progress views       |Design             |Add daily/7-day/30-day trend switching + date-specific calendar. Design for prominent placement.                                                                  |
|**MEDIUM**     |F6: Meds screen should support logging         |Design             |Add logging entry point from meds section — make calendar “today” date tappable to initiate injection flow. Users’ instinct reveals a natural primary entry point.|
|**MEDIUM**     |F8: Reflections adoption strategy              |Strategy           |Implement bedtime push notifications. Leverage catch-up logging as practical hook. Frame as optional, high-value for the right user.                              |
|**MEDIUM**     |F5: Nutritional display — show both by default |Design             |Combine calorie numbers with qualitative nutrient descriptions. The “mode” becomes hiding calories, not choosing a view.                                          |
|**LOW**        |F11: Card icon/button affordance               |Design             |Move CTA above fold or make icon tappable.                                                                                                                        |
|**LOW**        |F7: Learning pathways discoverability          |Design             |Addressed by F1 (bottom nav visibility). Content and format are validated.                                                                                        |
|**OBSERVATION**|P07 paradox (IA validation)                    |Context            |Architecture is sound. Navigation problems are styling, not structure.                                                                                            |
|**OBSERVATION**|AI Coach labeling/mental model                 |Context            |Monitor in pilot. May resolve with multi-day use.                                                                                                                 |
|**OBSERVATION**|Target demographic validation                  |Context            |Women 50-65 can and will use this app effectively.                                                                                                                |

-----

### VIII. CURATED QUOTE BANK — Report-Ready

Organized by theme for slide integration. Flag 🎥 indicates quotes that would benefit from a Dovetail video clip embed in the presentation.

#### A. App Value Proposition — Participants Articulating the Concept

|ID |Quote                                                                                                                                                                                      |Context                                           |🎥?   |
|---|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|-----|
|P07|“It’s easy to take the medication and lose weight, but you have to change your lifestyle.” [53:48]                                                                                         |Final thought — articulates the entire app concept|🎥 Yes|
|P07|“It would be great if the advertising could be geared towards tracking your journey, because this is not something you’re just gonna lose weight on. You have to modify your life.” [52:52]|Positioning recommendation                        |🎥 Yes|
|P04|“It’s a nutritional app, it’s a fitness app, it’s everything wrapped up in one… I would highly recommend it.” [48:26]                                                                      |Strongest overall endorsement                     |🎥 Yes|
|P05|“This looks like it kind of combines a lot, like more than one app.” [10:40]                                                                                                               |First impression — consolidation value            |     |
|P03|“I would definitely consider replacing the one I use with this and use this instead.” [52:34]                                                                                              |From the most critical participant                |🎥 Yes|
|P07|“For someone taking this medication to be able to track their entire wellness.” [13:14]                                                                                                    |App purpose articulated                           |     |

#### B. Delight Moments — Photo Meal Logging

|ID |Quote                                                                                                                            |Context                           |🎥?   |
|---|---------------------------------------------------------------------------------------------------------------------------------|----------------------------------|-----|
|P02|“I didn’t think it was gonna pick up the whole meal the way it did, so that was pretty cool.” [20:38]                            |AI recognition surprise           |🎥 Yes|
|P04|“If I could take a picture of it, I would do it all the time.” [20:23]                                                           |Photo as adoption gatekeeper      |🎥 Yes|
|P04|“I will admit to being lazy for logging food. Putting it in every single piece of it takes so long that it turns me off.” [17:20]|Why photo matters — effort barrier|     |
|P02|“I thought I was gonna have to search like the chicken and the tomatoes and the shaved carrots.” [19:30]                         |Expectation vs. reality gap       |     |
|P05|“That’s really cool, actually.” [24:26]                                                                                          |Genuine delight                   |🎥 Yes|
|P06|“I kind of figured with all of AI’s advancements that it would probably allow me to take a photo, and it did.” [20:11]           |Expected it — still appreciated   |     |

#### C. Delight Moments — Body Map / Injection Tracking

|ID |Quote                                                                                                              |Context                          |🎥?   |
|---|-------------------------------------------------------------------------------------------------------------------|---------------------------------|-----|
|P02|“This is a lot better because the app that I use, I think it only tracks my infusions.” [15:46]                    |Direct competitor comparison     |🎥 Yes|
|P02|“I didn’t expect to have like prior injection sites… which is good.” [15:19]                                       |Positive surprise                |     |
|P01|“It was better than expected… typically it would just be like, yes, today, right arm.” [20:07]                     |Better than text/dropdown        |     |
|P05|“I like that it tells you where your last one was because in [my app] I actually have to go back and look.” [22:21]|Competitive advantage over Shotzy|     |
|P02|“Sometimes I tend to forget… I think I did the repetitive side like 2 weeks in a row.” [08:30]                     |The pain point the feature solves|🎥 Yes|

#### D. AI Coach — Value & Emotional Connection

|ID |Quote                                                                                                                                                     |Context                          |🎥?   |
|---|----------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------|-----|
|P05|“I personally don’t have anyone that I’m going through like a weight loss journey with. So it’s just me, myself, and I.” [38:22]                          |AI as companion — emotional core |🎥 Yes|
|P07|“It’s focused on this app and what I’m going through. I don’t have to tell it that I’m taking a GLP-1.” [30:04]                                           |Contextual AI advantage          |🎥 Yes|
|P04|“The screens feel more natural, but I like the idea of talking to the coach because I like the feedback.” [28:48]                                         |Chat vs. UI — the nuanced view   |🎥 Yes|
|P04|“Especially once it starts getting to know me as well, it will know what I would eat more of.” [26:56]                                                    |AI personalization expectation   |     |
|P01|“This is helpful overall just to be able to ask those questions without having to call your doctor.” [33:43]                                              |AI as doctor-visit supplement    |     |
|P03|“I love it, love it. Look at that, it gives you some ideas for dinner.” [27:54]                                                                           |Delight with food recommendations|🎥 Yes|
|P05|“If I was first starting out, I would prefer [chat] because it gives you coaching. But once you’re in the rhythm, just going to the body diagram.” [42:29]|Temporal chat-vs-UI model        |     |

#### E. AI Coach — Labeling & Discoverability Problem

|ID |Quote                                                                                                                            |Context                        |🎥?   |
|---|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------|-----|
|P04|“The coach — is it a tutorial? Is it a more descriptive part of the app? Is it something giving you pep? Pumping you up?” [09:44]|Clearest labeling confusion    |🎥 Yes|
|P04|“I just didn’t think about that. I wasn’t sure what the coach was.” [23:25]                                                      |Why she didn’t find Coach in T4|     |
|P02|“At first I thought it was like a customer service type thing.” [31:49]                                                          |Mental model mismatch          |     |
|P04|“I would say like a 5 because it was easy to find, but I have to get used to using AI.” [25:45]                                  |SEQ reflects AI comfort, not UI|     |

#### F. Visual Differentiation — F1 Evidence Chain

|ID |Quote                                                                                                         |Context                                |🎥?   |
|---|--------------------------------------------------------------------------------------------------------------|---------------------------------------|-----|
|P01|“It all just blurs together, like blends, it doesn’t really stick out.” [06:52]                               |Apple Health complaint — foreshadows F1|🎥 Yes|
|P05|“I just didn’t even think to look along the bottom to see that there was a learning section.” [49:25]         |F1 smoking gun — bottom nav invisible  |🎥 Yes|
|P05|“Oh wait, hold on. Learn. Okay. Duh.” [47:45]                                                                 |Recognition-vs-recall moment           |🎥 Yes|
|P02|“Maybe it’s the way it looks all together.” [45:35]                                                           |Why reflection card wasn’t noticed     |     |
|P04|“I did not know it was done until I knew it was done.” [15:22]                                                |Toast notification failure             |🎥 Yes|
|P06|“I kind of wish under injection day it would say ‘last logged,’ so you know it went through for sure.” [15:35]|Persistent confirmation request        |     |
|P07|“The actual box on the app went away after I logged it. Visually telling me you’ve logged that.” [32:29]      |Card disappearance as confirmation     |     |

#### G. Reflections — The Full Spectrum

|ID |Quote                                                                                                                    |Context                           |🎥?   |
|---|-------------------------------------------------------------------------------------------------------------------------|----------------------------------|-----|
|P04|“I am a big gratitude journal person… I would absolutely keep it like this. All in one place.” [37:44]                   |Strongest endorsement             |🎥 Yes|
|P01|“I hate this.” [51:46]                                                                                                   |Strongest rejection               |🎥 Yes|
|P01|“I’d rather be like, babe, I’m feeling down, tell me something to make me feel better.” [52:50]                          |Competing with human connection   |     |
|P01|“I actually like [the app] though.” [53:01]                                                                              |Rejection ≠ app rejection         |🎥 Yes|
|P07|“I would more likely do it if it prompted me at the end of the day.” [45:46]                                             |Adoption driver: push notification|     |
|P05|“I would have to make a conscious effort to start doing, but if it made me feel good, I would probably continue.” [57:17]|Conditional adoption              |     |
|P03|“It’s natural to ask the questions. Whether I would have an answer, I don’t know.” [41:18]                               |Good questions, no habit          |     |

#### H. Learning Pathways — Content & Format

|ID |Quote                                                                                                                                    |Context                       |🎥?   |
|---|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------|-----|
|P02|“When you bunch a list together, kind of like scrambles your brain. This one separates it so it’s like individualized.” [38:13]          |Pathway format endorsement    |🎥 Yes|
|P03|“This is great information that you don’t always have.” [33:47]                                                                          |Content value                 |     |
|P03|“It took me a long time to navigate to where I currently am… but for somebody who is new, absolutely.” [36:49–37:13]                     |Experience-dependent relevance|     |
|P07|“It would be a toss-up between going here and asking the chatbot. It gives people options if you’re not an AI type person.” [39:50–40:19]|Learn as non-AI alternative   |     |

#### I. Navigation & Meds Screen

|ID |Quote                                                                                                                                               |Context                                |🎥?   |
|---|----------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------|-----|
|P07|“It literally says meds. So I would have expected that if I went there, that would have been an option.” [17:52]                                    |Meds screen expectation — clearest     |🎥 Yes|
|P03|“Well I learned not to hit those.” [18:03]                                                                                                          |Learning transfer from T2 to T3        |🎥 Yes|
|P01|“It’s kind of self-explanatory because it has the plus sign… if I need to add something or log something, I would be hitting the plus sign.” [18:22]|Only participant to articulate + button|     |
|P03|“It’s quicker. You don’t have to actually type a question.” [30:09]                                                                                 |Why button > AI for routine tasks      |     |

#### J. Target Demographic & Accessibility

|ID |Quote                                                                                                        |Context                                                            |🎥?   |
|---|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------|-----|
|P07|“There’s always some apps that challenge me. Maybe they’re not as intuitive to me.” [03:46]                  |Self-assessed tech discomfort — then navigated everything perfectly|🎥 Yes|
|P07|“I like the fact that there’s a coach button down the bottom.” [10:24]                                       |Noticed bottom nav that 3 others missed                            |     |
|P07|“I’m the kind of person who X’s out of things by mistake because I can’t figure out how to get back.” [50:34]|Self-aware — still navigated perfectly                             |     |
|P05|“Is this something that would be an app you would purchase?” [60:38]                                         |Unprompted purchase intent                                         |🎥 Yes|

#### K. Real-World Use Cases & Competitive Advantage

|ID |Quote                                                                                                                                                                                      |Context                                       |🎥?   |
|---|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------|-----|
|P01|“Even if the doctor asks ‘oh what day?’ And I’m assuming you can put side effects… opposed to just like, ‘Yeah, everything is good,’ when some things did happen, you just forgot.” [21:30]|Doctor visit use case                         |     |
|P02|“The app that I use, I tried to add my GLP-1 to that, but I couldn’t. So I’m interested in this app.” [08:00]                                                                              |Unmet need — existing apps don’t support GLP-1|🎥 Yes|
|P04|“Copy it, paste it into the Giant app, and I’m good to go.” [44:11]                                                                                                                        |Shopping list real-world integration          |     |
|P04|“I’m not one who likes to cook with more than 5 ingredients, so it’ll start to pick up on that.” [49:09]                                                                                   |AI personalization expectation                |     |
|P02|“Most everybody has a cell phone in their hand anyway when they’re eating most of the time.” [25:16]                                                                                       |Daily tracking acceptance                     |     |

-----

## PHASE 4: REPORT BLUEPRINT

**Complete slide-by-slide blueprint (v2) generated at:** /home/claude/presentation_blueprint_v2.md
**Calibrated against:** BI X A/B Testing Research Readout (SurvoPlus, Dec 2025) — accessed at coderift.io/Research_Readout_AB_Testing.pdf
**Structure:** 38 main slides + 6 appendix across 7 sections
**Narrative arc:** Front matter → Executive summary (combined study context + top 3 insights + anchor quote) → What resonated with users (front-loaded wins with 🎥 video clips, competitive comparison, value proposition quotes) → Task-by-task results (SEQ bar chart, completion table, satisfaction radar, prototype context) → Design findings & opportunities (6 findings, each with evidence chain, visualization, and two-column implications/recommendations) → Recommendations (tiered priority matrix: fix before / enhance for / monitor during diary study) → Closing (participants make the business case)

-----

## PROTOTYPE LIMITATIONS LEDGER

**Context:** The prototype was a Lovable-built interactive PWA with live AI integration. It functioned as a near-complete interactive frontend, not a Figma clickthrough. Participants treated it as a real app. However, some features were inconsistent or non-functional due to prototype constraints. The following must be tagged as **prototype limitations, not design issues** whenever they appear in participant data.

|#  |Limitation                                                                                                                                                                                                                                          |Impact                                                                                                                                                                                                   |How to Tag in Report                                                                                                                                                                                                                         |
|---|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|PL1|**Chat-based logging inconsistent.** AI Coach should handle logging (meals, medication, side effects, etc.) inline, but Lovable’s AI responses were inconsistent — sometimes it worked, sometimes it redirected users to the + button or UI screens.|Inconsistent across participants (worked for P04, failed for P02).                                                                                                                                       |**General note only — not a finding. Chat-based logging was validated in the MVP phase and will be fully functional in the production app. Any participant friction related to chat logging should be excluded from design recommendations.**|
|PL2|**Microphone icon non-functional.** The mic button in AI Coach was present in the UI but not wired up.                                                                                                                                              |P05 and P07 both tried to use it. P07 specifically said she’d prefer voice interaction. This is a real user need surfaced by the prototype, but the “frustration” of it not working is a prototype issue.|“Voice input was present in the UI but non-functional in the prototype. Two participants attempted to use it, confirming demand for voice-based interaction.”                                                                                |
|PL3|**Dose customization not functional.** Medication logging used persona data with a fixed dose. Users could not change dosage. In production, this would likely be tied to the user’s prescription.                                                  |P01 and P04 both tried to change the dose. This is expected behavior that the prototype couldn’t support.                                                                                                |“Dose was fixed in the prototype. Production app will pull from prescription data.”                                                                                                                                                          |
|PL4|**AI chat responses variable.** Because Lovable’s AI was live (not scripted), response quality varied based on how participants phrased queries and the AI’s own variability.                                                                       |May explain some of the SEQ spread on T4 (range 4–7). A participant who got a great AI response would rate higher than one who got a mediocre one, independent of the UI design.                         |“AI responses were live and unscripted, introducing natural variability across sessions.”                                                                                                                                                    |

**NOT a prototype limitation (valid design finding):**

- **Meal logging card icon vs. button confusion (P04).** The card had a decorative icon above the fold that participants mistook for the tappable button, while the actual button was below the fold. This is a real UI issue — the icon affordance needs to be clarified or the button needs to be above the fold.

-----

## APPENDIX: DATA SOURCE CROSS-REFERENCE

|Data Source              |Location                                                                                                                                                                                          |Status                                                                                                                                                                                                                                            |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|Rainbow Grid (rotated)   |BI_X_Testing_Notes.xlsx → “Rainbow Grid” tab                                                                                                                                                      |✅ Processed                                                                                                                                                                                                                                       |
|Observer Notes — Allen   |BI_X_Testing_Notes.xlsx → “Notes — Observer 2” and “Notes — Observer 3” tabs                                                                                                                      |✅ Processed                                                                                                                                                                                                                                       |
|Observer Notes — Lisa    |BI_X_Testing_Notes.xlsx → “Notes — Observer 1” tab                                                                                                                                                |✅ Processed                                                                                                                                                                                                                                       |
|End of Day Synthesis     |BI_X_Testing_Notes.xlsx → “End of Day Synthesis” tab                                                                                                                                              |✅ Processed                                                                                                                                                                                                                                       |
|Demographics             |BOEH2255_Data_sheet.xlsx → “Demographics” tab                                                                                                                                                     |✅ Processed                                                                                                                                                                                                                                       |
|Facilitator Session Data |BOEH2255_Data_sheet.xlsx → “Session Data” tab                                                                                                                                                     |✅ Processed                                                                                                                                                                                                                                       |
|Raw Transcripts (P01-P07)|Not yet provided                                                                                                                                                                                  |⬜ Pending                                                                                                                                                                                                                                         |
|Dovetail Summaries       |P02 summary reviewed as calibration                                                                                                                                                               |✅ Processed (confirmatory)                                                                                                                                                                                                                        |
|Dovetail Insight Docs    |Toast notifications, micro-hesitations, top 10 pain points, top 10 themes                                                                                                                         |✅ Processed                                                                                                                                                                                                                                       |
|Prototype Screenshots    |Home screen, meds popover, body map, toast notification, nutrition screen (F11 card), calorie view, guided nutrition view, Learn overview, Learn pathway detail, evening view, reflection workflow|✅ Reviewed — confirmed F1 visual differentiation root cause, F6 meds calendar affordance, F11 card icon/button confusion, toast notification styling, and bottom nav invisibility. Screenshots ground all visual findings in specific UI elements.|
