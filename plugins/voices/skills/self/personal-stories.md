# Personal Stories Reference

**Purpose:** An optional library of personal stories, anecdotes, and experiences to use when they strengthen content. Not every piece needs a personal story - use them when they add credibility, relatability, or concrete examples to abstract points.

**Use stories when:**
- Teaching through example
- Building credibility
- Making abstract concepts concrete
- Creating emotional connection

**Skip stories when:**
- The point is already clear and strong
- Content is brief/quick-hit
- You're already being story-driven

---

## Early Years & Family Business

### Started in the Family Restaurant at Age 12
Working in my parents' first restaurant from age 12, learning the business from the floor up. By 18, I was managing it - real customers, real staff, real bills, real consequences. That was my business education.

**Key Themes:** Hands-on learning, real-world education vs. theory, early responsibility
**When to Use:** Establishing credibility, contrasting theory vs. practice, showing long-term industry experience
**Emotional Tone:** Grounded, matter-of-fact, foundational

---

### Mom's Excel Spreadsheets
My mother's meticulously organized Excel spreadsheets from the family restaurant - formulas for variance calculations, color-coded cells for quick scanning, separate tabs for weekly summaries. She taught me how to track every penny. That knowledge was gold and served me across multiple businesses for decades.

**The Pivot:** But the days of manual data entry are over. Understanding *what* to track is timeless - sitting there typing numbers into cells every night is yesterday's game.

**Key Themes:** Respecting tradition while embracing innovation, foundational skills, generational business knowledge
**When to Use:** Teaching automation (honoring the past while moving forward), explaining why tracking matters but manual entry doesn't
**Emotional Tone:** Warm, respectful, forward-looking

---

### The Mint Chocolate Chip Lesson (Age 14)
At 14, I ate so much mint chocolate chip ice cream working at the restaurant that I felt sick for a full day. My cholesterol was through the roof.

**Key Themes:** Learning through mistakes, the physical reality of restaurant work, youthful excess
**When to Use:** Light humor, showing vulnerability, discussing restaurant health challenges
**Emotional Tone:** Self-deprecating, humorous

---

## First Business Ventures

### The Lazy Loon Gift Co. at Age 22
At 22, I wrote my first business plan, walked into the bank on my own, and secured financing to open The Lazy Loon Gift Co., a tourist giftware shop. My first taste of building something from zero - and my first lesson that confidence usually shows up *after* you do the scary thing.

**Key Themes:** Taking action despite fear, entrepreneurial courage, learning by doing
**When to Use:** Encouraging action over overthinking, discussing fear and confidence, first-time business creation
**Emotional Tone:** Empowering, encouraging, honest about fear

---

### Designing and Building a Gas Station (2005)
In 2005, I designed, branded, and built a gas station and convenience store from the ground up. Full vision to execution.

**Key Themes:** Large-scale project execution, branding, comprehensive business building
**When to Use:** Establishing credibility for big thinking, discussing branding and design, showing range of experience
**Emotional Tone:** Confident, capable

---

### The Subway Franchise - 12 Years, Top Sales
Operated a Subway franchise for 12 years and drove it to top sales in my region. Consistent execution and operational excellence over time.

**Key Themes:** Long-term consistency, competitive success, operational mastery, franchise systems
**When to Use:** Discussing consistency, systems, long-term commitment, competitive performance
**Emotional Tone:** Proud but humble, matter-of-fact success

---

### Rise to Fries - Family Tradition
Created Rise to Fries from scratch - my own quick-serve brand rooted in family tradition and famous for Aunt Bella's secret sauce. Simple product, sharp execution: quality, speed, consistency, and a team that can handle the rush.

**Key Themes:** Family legacy, building from scratch, simple but excellent execution
**When to Use:** Discussing brand creation, family business, operational excellence, simplicity
**Emotional Tone:** Warm, proud, grounded

---

## Restaurant Operations Stories

### The 11 PM Cash Sheet Reality
It's 11 PM. The fryers are finally off. The last customer has left. Your feet are screaming. And you still have to sit down and manually enter the day's cash drawer totals, credit card batches, and sales numbers into spreadsheets. Every. Single. Day.

**Before Automation:** 15-20 minutes every single night. Multiply that by 365 days... that's like two full weeks of work I could be spending literally anywhere else.

**Key Themes:** Exhaustion, repetitive tasks, late-night grind, time waste
**When to Use:** Introducing automation benefits, painting the before-picture, showing empathy for operator reality
**Emotional Tone:** Exhausted but relatable, sets up relief/solution

---

### Chief Officer of Everything
You become the Chief Officer of Everything: hiring, training, scheduling, ordering, marketing, bookkeeping, repairs, and yes - the glamorous stuff like fixing toilets and dealing with grease and chaos on a random Tuesday afternoon.

**Key Themes:** Overwhelm, wearing too many hats, unglamorous reality
**When to Use:** Describing burnout, validating operator reality, setting up need for leverage/systems
**Emotional Tone:** Frustrated but humorous, validating

---

### The Grease and Chaos
The work is physical and messy (hello, deep fryers and grease). Staffing can be a nightmare - especially with younger workers who may start and quit quickly.

**Key Themes:** Physical demands, staffing challenges, messy reality
**When to Use:** Keeping it real about restaurant work, discussing labor challenges
**Emotional Tone:** Blunt, honest

---

### Why It's Rewarding
You get to build a place people love. You get to create jobs. You get to turn an idea into a real thing that feeds families - including your own.

**Key Themes:** Purpose, community impact, tangible results, legacy
**When to Use:** Balancing hard truths with meaning, showing why people stay in the industry
**Emotional Tone:** Warm, meaningful, grounded

---

## Learning Journeys (AI & Automation)

### The N8N Automation Journey - Full Story

**Level 1: "What's a Node?" Phase**
Simple goal: Get my daily email (with .txt attachment of cash-out numbers), pull specific values, put them into Google Sheets. Sounds simple, right?

Claude gave me the basic structure: Gmail Trigger → Extract attachment → Parse .txt file → Send to Google Sheets.

I thought, "Oh okay, I got this!"

Friends... I did not got this. 😅

**Level 2: "Error Messages Are My New Best Friend" Phase**
Setting up N8N felt like learning a new language. Everything is called a "node." You connect nodes together.

First roadblock: The Gmail Trigger node.
Second roadblock: The Code node - JavaScript to extract values. I've written spreadsheet formulas, but regex patterns? Buffer encoding? Binary data? I was in over my head faster than fries hit the fryer.

First major error:
```
**Problem in node 'Extract Values from TXT'**
Cannot read properties of undefined (reading 'data0')
```

This was where most people would quit. But I've run restaurants. I've dealt with suppliers showing up with the wrong order. I've handled health inspectors. I've survived the 2020 pandemic shutdowns. I can debug a JavaScript node.

Claude helped me fix it. It worked! Well... it extracted the data.

**Level 3: "Weekly Date Matching Nightmare" Phase**
My Google Sheet isn't just rows of dates. It's organized by weeks within the month:
- Week 1: Oct 1-7 (cells in one section)
- Week 2: Oct 8-14 (cells in another section)
- Week 3: Oct 15-21 (cells in yet another section)

Every day's email needs to:
1. Figure out what date it is
2. Determine which week that falls into
3. Find the correct column in that week's section
4. Put the data there

This part took DAYS to figure out.

**The Debugging Montage:**
- Attempt 1: Dates extracted wrong (showed up as "undefined")
- Attempt 2: Found the date, but couldn't match to the right week
- Attempt 3: Matched the week, but wrote to the wrong column
- Attempt 4: Everything worked... for Week 1. Week 2 broke everything.
- Attempt 5: Finally got dynamic week detection working!

Each failure taught me something. Each error message led to a small breakthrough.

**Level 4: "September Emails Keep Breaking My October Workflow" Phase**
My Gmail had unread Cash Out Report emails from September. The workflow would try to process them, fail (September data doesn't match October's week structure), crash, and loop.

The Solution? Claude suggested complex error handling to skip old emails OR just manually mark all September emails as read once.

I chose the simple solution. Sometimes the simplest solution is the best solution. (This is also true for restaurant management.)

**Level 5: "IT ACTUALLY WORKS!" Moment**
After 3-4 days of tinkering, I had a working workflow:
✅ Monitors Gmail for "Cash Out Report" emails
✅ Downloads the .txt attachment
✅ Extracts the date and figures out which week it belongs to
✅ Parses all the values (Cash, MC, Visa, Debit, Net Sales)
✅ Finds the correct column in Google Sheets
✅ Writes each value to the right cell
✅ Marks the email as read
✅ Runs every hour automatically

The first time it ran successfully and I saw the data appear in my spreadsheet... I'm not gonna lie, I got a little emotional. 😅

**The Result:**
- That 15-20 minutes every night? **Gone.**
- Mental load of "oh no, I forgot to enter yesterday's numbers"? **Gone.**
- Possibility of typos messing up monthly reports? **Gone.**

This workflow saves me **over 90 hours a year.** That's more than two full work weeks.

**Key Themes:** Struggle to breakthrough, learning through errors, persistence, simple solutions, specific results, permission-giving
**When to Use:** Teaching automation, showing the messy reality, encouraging non-technical operators, proving ROI
**Emotional Tone:** Vulnerable, humorous, triumphant, encouraging

---

### "How Hard Could It Be?" Confidence
"'How hard could it be?' I thought, with the confidence of someone who once managed a Subway to highest sales in the region."

*Narrator: It was, in fact, quite hard. Very hard. Surprisingly hard.*

**Key Themes:** Overconfidence, learning humility, humor
**When to Use:** Self-deprecation, showing the gap between expectation and reality
**Emotional Tone:** Humorous, self-aware

---

### The Sheridan College Non-Graduation
I attended Sheridan College for business years ago, and I didn't graduate in my last semester because, at the time, I thought I knew everything. Then I opened businesses and realized how little school can prepare you for the day-to-day realities: long hours for no pay, constant decision fatigue, and the fact that problems don't wait for a convenient moment.

**Key Themes:** Humility, real-world learning vs. academic, learning through mistakes
**When to Use:** Contrasting theory and practice, showing humility, discussing real business education
**Emotional Tone:** Honest, humble, reflective

---

## Mistakes & Hard Lessons

### Mother's Passing - Changing Everything
After the success of the convenience store, my mother passed away suddenly, and my father and I never felt the same about the business again. We kept going, but it changed how we looked at everything.

**Key Themes:** Loss, motivation shift, perseverance through grief
**When to Use:** Showing humanity, discussing why people stay or leave businesses, honoring emotional reality
**Emotional Tone:** Somber, honest, human

---

### The Online Business Experiment
We experimented with other directions, including online business. I assumed I could translate my brick-and-mortar experience directly, but it didn't work out quite the way I expected. I bought into a business I didn't understand and had little passion for, and I struggled with it for years.

**Key Themes:** Failed experiments, passion matters, transferability limits
**When to Use:** Discussing failures, showing vulnerability, cautioning against assumptions
**Emotional Tone:** Honest, reflective, cautionary

---

### Competition and Market Downturns
Meanwhile, competition hit harder than ever, and sales dropped to all-time lows over time. When the Canadian dollar is low and travel is down, you feel it - especially in businesses that depend on traffic and timing. That's the truth about business: it has seasons, and nothing stays easy for long.

**Key Themes:** Market forces, seasons of business, external factors
**When to Use:** Discussing market realities, preparing for cycles, honest business talk
**Emotional Tone:** Blunt, realistic, experienced

---

### "Do What You Love" Doesn't Pay Invoices
A lot of people say "do what you love." I don't fully buy that. You have to do what makes you money - because love doesn't pay invoices. Doing what you love isn't a hobby; it's still work, and it never really stops. Business demands consistency: you show up, repeat the fundamentals, and keep adjusting.

**Key Themes:** Pragmatism over passion, business reality, anti-platitude
**When to Use:** Pushing back on naive business advice, setting realistic expectations
**Emotional Tone:** Direct, contrarian, grounded

---

### Detours Are Teachers
I made plenty of mistakes - and honestly, they taught me more than my successes.

**Key Themes:** Learning from failure, growth through mistakes
**When to Use:** Normalizing failure, encouraging resilience
**Emotional Tone:** Reflective, encouraging

---

## Breakthrough Moments

### The First Successful Automation
The first time it ran successfully and I saw the data appear in my spreadsheet... I'm not gonna lie, I got a little emotional. 😅

**Key Themes:** Victory, validation, emotion of breakthrough
**When to Use:** Celebrating wins, showing the human side of success
**Emotional Tone:** Triumphant, vulnerable, joyful

---

### Not Thinking About It Anymore
A few weeks after getting this working, I realized something: I haven't thought about manually entering cash sheet data in over a month. The automation just... works. Every day. Quietly. Reliably.

It's like having the world's most consistent employee who never calls in sick, never makes mistakes, and works for free.

**Key Themes:** Compounding relief, set-it-and-forget-it success, peace of mind
**When to Use:** Describing the after-state of automation, showing long-term benefits
**Emotional Tone:** Relieved, satisfied, peaceful

---

### Seeing Automation Opportunities Everywhere
Now I'm working on automating other parts of the business. Because once you get that first automation working, you start seeing automation opportunities EVERYWHERE.

**Key Themes:** Momentum, paradigm shift, expanding possibilities
**When to Use:** Encouraging people to start small, showing how mindset shifts
**Emotional Tone:** Excited, energized, forward-looking

---

## Personal Life Context

### Member of Chief and Council - First Nation Community
I'm a member of Chief and Council in a First Nation community. This is part of my identity and service beyond business.

**Key Themes:** Community leadership, service, broader identity
**When to Use:** Establishing full identity, showing community commitment
**Emotional Tone:** Proud, service-oriented

---

### Parent, Water Lover, Lifelong Learner
I'm a parent, I love being on the water, and I'm always learning - including interests like tiger conservation. Life is full, and that's exactly why time-saving systems matter.

**Key Themes:** Full life, diverse interests, why time matters
**When to Use:** Showing humanity, explaining motivation for efficiency
**Emotional Tone:** Warm, curious, purposeful

---

## Quick Proof Points & Credibility Snapshots

Use these when you need fast credibility markers:

- Built and operated multiple businesses from concept to day-to-day operations (food service, retail, franchising)
- Secured business financing independently starting at age 22
- Designed, branded, and built a gas station and convenience store (2005)
- Operated a Subway franchise for 12 years and led it to top sales in region
- Created Rise to Fries from scratch - brand, menu, customer experience
- Interviewed and employed 100+ people; built team culture from ground up
- Designed spreadsheets, marketing campaigns, operational systems before AI existed
- Rebranded and renovated locations to modernize customer experience
- Self-taught N8N and Claude automation with zero coding background
- Single automation reclaimed 90 hours/year (two full work weeks)

---

## How to Use This File

**When a personal story would strengthen your content:**

1. **Identify the point you're making** (automation saves time, learning is messy, start simple, etc.)
2. **Check if a matching story exists** that illustrates it
3. **If it fits naturally, use it briefly** - don't over-explain
4. **Extract the lesson** - connect back to the point
5. **Move forward** - stories support points, they don't replace them

**Not every piece needs a personal story.** Use them when they add value, not out of obligation.

**Story Selection Tips:**

- **For credibility:** Early years, Subway success, Rise to Fries, business building
- **For empathy/relatability:** 11 PM cash sheets, Chief Officer of Everything, grease and chaos
- **For encouragement:** First business at 22, N8N breakthrough, automation opportunities everywhere
- **For vulnerability:** Sheridan non-graduation, online business failure, "I did not got this"
- **For teaching:** N8N journey (full levels), simple solutions, error messages as teachers
- **For contrarian takes:** "Do what you love" pushback, school vs. real world

**Formatting Stories in Content:**

- Use first person ("I")
- Keep them concise (3-5 sentences for quick anecdotes, longer for teaching narratives)
- Lead with sensory details when scene-setting
- Use italics for narrator voice asides
- End with the lesson or transition to the next point

---

## Stories Still Needed

**Add stories for these areas when you find/remember them:**

- [ ] Specific staffing disasters/wins
- [ ] Customer service moments (good and bad)
- [ ] Equipment breakdown stories
- [ ] Inventory mistakes that taught lessons
- [ ] Marketing campaigns that worked (or didn't)
- [ ] Financial close calls or breakthroughs
- [ ] Pandemic survival stories
- [ ] First AI "aha" moments before N8N
- [ ] Specific time-saving automations beyond cash sheets
- [ ] Community/family business moments
- [ ] Teaching/mentoring other operators

**To add a new story:**

1. Choose the appropriate category
2. Give it a descriptive title
3. Write the story (2-10 sentences depending on complexity)
4. Add Key Themes
5. Add When to Use
6. Add Emotional Tone
