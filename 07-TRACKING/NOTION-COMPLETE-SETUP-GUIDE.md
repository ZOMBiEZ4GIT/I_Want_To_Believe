# NOTION COMPLETE SETUP GUIDE
## Comprehensive Database Structure for ADHD Podcast Production System

**This guide provides complete specifications for setting up the entire I Want To Believe podcast production system in Notion.**

---

## TABLE OF CONTENTS

1. [Overview](#overview)
2. [Database Structures](#database-structures)
3. [Database Relations](#database-relations)
4. [Views Configuration](#views-configuration)
5. [Formulas & Rollups](#formulas--rollups)
6. [Dashboard Setup](#dashboard-setup)
7. [Import Instructions](#import-instructions)
8. [Automation & Templates](#automation--templates)
9. [Mobile Workflow](#mobile-workflow)
10. [Quick Reference](#quick-reference)

---

## OVERVIEW

### What You'll Create

**5 Main Databases:**
1. **Episodes** - All 100 episodes with tracking
2. **Tasks** - Brain-state-based task lists
3. **Achievements** - XP tracking and badges
4. **Weekly Planning** - Recording schedule
5. **Progress Log** - Daily activity tracking

**1 Master Dashboard:**
- Progress overview
- Current level & XP
- This week's focus
- Quick actions
- Motivation stats

---

## DATABASE STRUCTURES

### 1. EPISODES DATABASE

**Database Name:** `📺 Episodes`

#### Properties:

| Property Name | Type | Configuration |
|--------------|------|---------------|
| **Episode Title** | Title | (default) |
| **Number** | Number | Format: 001 |
| **Status** | Select | Options: Not Started, Prep, Recording, Editing, Complete, Published |
| **Category** | Multi-select | Options: UFO Sighting, Abduction, Ancient Mystery, Government, X-Files, UAP/Modern, Physical Evidence, Whistleblower, Media/Culture, Documents/Hoax |
| **Difficulty** | Select | Options: ⭐, ⭐⭐, ⭐⭐⭐, ⭐⭐⭐⭐, ⭐⭐⭐⭐⭐ |
| **Fun Factor** | Select | Options: 🎉, 🎉🎉, 🎉🎉🎉, 🎉🎉🎉🎉, 🎉🎉🎉🎉🎉 |
| **Estimated Time** | Number | In hours (e.g., 3.5) |
| **Actual Time** | Number | In hours - track as you go |
| **Recording Date** | Date | When you recorded it |
| **Editing Date** | Date | When you edited it |
| **Published Date** | Date | When you published it |
| **XP Earned** | Number | Total XP for this episode |
| **Self Rating** | Select | Options: ⭐, ⭐⭐, ⭐⭐⭐, ⭐⭐⭐⭐, ⭐⭐⭐⭐⭐ |
| **Audio File** | Files & Media | Upload final MP3 |
| **Episode Brief Read** | Checkbox | Did you read the brief? |
| **Framework Read** | Checkbox | Did you read the framework? |
| **Recording Notes Marked** | Checkbox | Did you mark up recording notes? |
| **Recorded** | Checkbox | Episode recorded? |
| **Edited** | Checkbox | Episode edited? |
| **Quality Check Done** | Checkbox | Final quality check? |
| **Notes** | Text | Your thoughts, lessons learned |
| **What Went Well** | Text | Celebrate successes |
| **What To Improve** | Text | Learn from challenges |
| **Related Episodes** | Relation | Link to other Episodes (prerequisites, follow-ups) |
| **Prerequisites** | Relation | Link to Episodes that should be listened to first |
| **Tasks** | Relation | Link to Tasks database |
| **Week Planned** | Relation | Link to Weekly Planning database |
| **Folder Path** | Text | `03-EPISODES/episode-XXX-[title]/` |
| **Brief Path** | Text | `EPISODE-BRIEF.md` |
| **Framework Path** | Text | `FULL-FRAMEWORK.md` |
| **Recording Notes Path** | Text | `RECORDING-NOTES.md` |
| **Tracker Path** | Text | `COMPLETION-TRACKER.md` |

#### Select Options Details:

**Status Colors:**
- Not Started: Gray
- Prep: Yellow
- Recording: Orange
- Editing: Blue
- Complete: Green
- Published: Purple

**Category Colors:**
- UFO Sighting: Red
- Abduction: Orange
- Ancient Mystery: Yellow
- Government: Blue
- X-Files: Purple
- UAP/Modern: Green
- Physical Evidence: Brown
- Whistleblower: Pink
- Media/Culture: Gray
- Documents/Hoax: Red

---

### 2. TASKS DATABASE

**Database Name:** `✅ Tasks`

#### Properties:

| Property Name | Type | Configuration |
|--------------|------|---------------|
| **Task Name** | Title | (default) |
| **Task Type** | Select | Options: 5-Minute, 15-Minute, 1-Hour, Learning, Recording, Editing, Publishing, Planning, Admin |
| **Brain State** | Select | Options: High Energy, Medium Energy, Low Energy, Zero Focus |
| **XP Value** | Number | XP earned for completing |
| **Completed** | Checkbox | Is task done? |
| **Completion Date** | Date | When completed |
| **Related Episode** | Relation | Link to Episodes database |
| **Time Required** | Number | In minutes |
| **Description** | Text | What to do |
| **Difficulty** | Select | Options: Easy, Medium, Hard |
| **Repeatable** | Checkbox | Can do this multiple times? |
| **Category** | Select | Options: Prep, Production, Post-Production, Admin, Skill-Building, Planning |

#### Pre-populated Task Templates:

**5-Minute Tasks:**
- Read one episode brief (10 XP, Low Energy)
- Update completion tracker (5 XP, Low Energy)
- Browse episode list (5 XP, Zero Focus)
- Practice one pronunciation (10 XP, Low Energy)
- Update progress visualization (5 XP, Low Energy)

**15-Minute Tasks:**
- Read episode brief + recording notes (25 XP, Medium Energy)
- Mark up recording notes (15 XP, Medium Energy)
- Record cold open (20 XP, Medium Energy)
- Edit one section (30 XP, Medium Energy)
- Plan next episode (15 XP, Medium Energy)

**1-Hour Tasks:**
- Record believer section (30 XP, High Energy)
- Record skeptic section (30 XP, High Energy)
- Complete episode edit (50 XP, High Energy)
- Deep research session (25 XP, High Energy)
- Batch prep 3 episodes (50 XP, High Energy)

---

### 3. ACHIEVEMENTS DATABASE

**Database Name:** `🏆 Achievements`

#### Properties:

| Property Name | Type | Configuration |
|--------------|------|---------------|
| **Achievement Name** | Title | (default) |
| **Type** | Select | Options: Milestone, Skill, Streak, Quality, Comeback, Special |
| **Badge Emoji** | Text | 🎙️, 🔥, 🎉, 🏆, 👑, etc. |
| **XP Bonus** | Number | Bonus XP awarded |
| **Unlocked** | Checkbox | Have you earned this? |
| **Unlock Date** | Date | When you earned it |
| **Requirements** | Text | What you need to do |
| **Description** | Text | What this achievement means |
| **Tier** | Select | Options: Bronze, Silver, Gold, Platinum, Legend |
| **Current Progress** | Number | How many/much so far |
| **Target** | Number | Goal to reach |

#### Pre-populated Achievements:

**Milestones:**
- 🎙️ First Episode (Episode 1 complete, 50 XP bonus)
- 🎙️🎙️🎙️ Trifecta (3 episodes complete, 75 XP)
- 🎙️ x10 Double Digits (10 episodes, 150 XP)
- 🎉 Quarter Century (25 episodes, 250 XP)
- 🏆 Halfway Hero (50 episodes, 500 XP)
- 🎯 Three-Quarter Champion (75 episodes, 750 XP)
- 👑 Legendary Complete (100 episodes, 1000 XP)

**Streaks:**
- 🔥 Hot Streak (7-day streak, 100 XP)
- 🔥🔥 On Fire (14-day streak, 200 XP)
- 🔥🔥🔥 Unstoppable (30-day streak, 500 XP)

**Skills:**
- 🎭 Voice Actor (Master character voices in 5+ episodes, 100 XP)
- ✂️ Editing Ninja (Cut editing time in half, 100 XP)
- 📝 Research Master (Deep-dive extra research 3+ times, 150 XP)
- ⚡ Hyperfocus Hero (Record 2 episodes in one day, 200 XP)

**Quality:**
- ⭐⭐⭐⭐⭐ First Perfect Episode (Self-rated 5/5, 50 XP)
- 🎯 Perfectionist Defeated (Published without excessive re-recording, 75 XP)

---

### 4. WEEKLY PLANNING DATABASE

**Database Name:** `📅 Weekly Planning`

#### Properties:

| Property Name | Type | Configuration |
|--------------|------|---------------|
| **Week Of** | Date | Week starting date |
| **Week Number** | Number | 1, 2, 3... |
| **Planned Episodes** | Relation | Link to Episodes database |
| **Actual Episodes** | Relation | Link to Episodes completed this week |
| **Goal** | Select | Options: 1 Episode, 2 Episodes, Catch Up, Learning Week, Rest Week |
| **Status** | Select | Options: Planning, In Progress, Complete, Partial |
| **Total XP Earned** | Rollup | Sum of XP from completed episodes |
| **Prep Day** | Select | Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday |
| **Recording Day** | Select | Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday |
| **Editing Day** | Select | Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday |
| **Notes** | Text | Weekly reflections |
| **Challenges** | Text | What was hard this week |
| **Wins** | Text | What went well |
| **Next Week Focus** | Text | Plan for next week |

---

### 5. PROGRESS LOG DATABASE

**Database Name:** `📊 Progress Log`

#### Properties:

| Property Name | Type | Configuration |
|--------------|------|---------------|
| **Date** | Date | Daily entry |
| **Tasks Completed** | Relation | Link to Tasks database |
| **Episodes Worked On** | Relation | Link to Episodes database |
| **XP Earned Today** | Number | Total XP for the day |
| **Brain State** | Select | Options: High Energy, Medium Energy, Low Energy, Zero Focus, Rest Day |
| **Time Spent** | Number | In hours |
| **What I Did** | Text | Summary of work |
| **Wins** | Text | Celebrate today's progress |
| **Challenges** | Text | What was difficult |
| **Tomorrow's Plan** | Text | What you'll do next |
| **Mood** | Select | Options: 😊 Great, 🙂 Good, 😐 Okay, 😔 Tough, 🛌 Need Rest |
| **Streak Day** | Number | Current streak count |

---

## DATABASE RELATIONS

### How Databases Connect:

**Episodes ↔ Tasks:**
- Each episode can have multiple tasks
- Tasks can be linked to specific episodes
- **Relation:** Two-way

**Episodes ↔ Episodes:**
- Prerequisites (what to listen to first)
- Related Episodes (similar topics)
- Follow-ups (continuation)
- **Relation:** Self-relation

**Episodes ↔ Weekly Planning:**
- Episodes planned for the week
- Episodes actually completed
- **Relation:** Two-way

**Tasks ↔ Progress Log:**
- Daily tasks completed
- Track what you actually did
- **Relation:** Two-way

**Episodes ↔ Progress Log:**
- Which episodes you worked on today
- Track daily episode progress
- **Relation:** Two-way

**Achievements ↔ Episodes:**
- Track which episodes unlocked achievements
- **Relation:** One-way (Achievements reference Episodes)

---

## VIEWS CONFIGURATION

### EPISODES DATABASE VIEWS

#### View 1: 📋 Kanban Board (Main View)
**Type:** Board
**Group By:** Status
**Filter:** None (show all)
**Sort:** Number (ascending)
**Properties Shown:** Number, Title, Difficulty, Fun Factor, Recording Date, XP Earned
**Card Preview:** Show first image
**Card Size:** Medium

**Purpose:** Drag episodes through your workflow

---

#### View 2: 📊 Table View (All Details)
**Type:** Table
**Filter:** None
**Sort:** Number (ascending)
**Properties Shown:** All
**Grouped:** No

**Purpose:** See all episode data at once

---

#### View 3: 📅 Calendar View
**Type:** Calendar
**Calendar By:** Recording Date
**Filter:** Status is not "Not Started"
**Properties Shown:** Number, Title, Status, Difficulty
**Color By:** Status

**Purpose:** Plan recording schedule

---

#### View 4: 🎯 Next Up (Most Important!)
**Type:** Table
**Filter:**
- Status is "Not Started" OR
- Status is "Prep"
**Sort:**
1. Fun Factor (descending)
2. Difficulty (ascending)
**Limit:** First 10 items
**Properties Shown:** Number, Title, Difficulty, Fun Factor, Estimated Time

**Purpose:** Quick episode selection

---

#### View 5: 🌟 Easiest First
**Type:** Gallery
**Filter:**
- Status is "Not Started"
- Difficulty is ⭐ OR ⭐⭐ OR ⭐⭐⭐
**Sort:**
1. Fun Factor (descending)
2. Difficulty (ascending)
**Properties Shown:** Number, Title, Difficulty, Fun Factor, Category
**Card Size:** Large
**Card Preview:** Show first image

**Purpose:** Find easiest episodes to build confidence

---

#### View 6: ✅ Completed
**Type:** Gallery
**Filter:** Status is "Complete" OR "Published"
**Sort:** Published Date (descending)
**Properties Shown:** Number, Title, Published Date, Self Rating, XP Earned
**Card Size:** Medium

**Purpose:** See your completed work (motivation!)

---

#### View 7: 🎬 In Production
**Type:** Table
**Filter:** Status is "Recording" OR "Editing"
**Sort:** Status (custom order: Recording, Editing)
**Properties Shown:** Number, Title, Status, Recording Date, Actual Time, Notes

**Purpose:** Focus on current work

---

### TASKS DATABASE VIEWS

#### View 1: 🧠 By Brain State
**Type:** Board
**Group By:** Brain State
**Filter:** Completed is unchecked
**Sort:** XP Value (descending)
**Properties Shown:** Task Name, Task Type, XP Value, Time Required

**Purpose:** Match tasks to your current energy

---

#### View 2: ⚡ Quick Wins (5-15 min)
**Type:** List
**Filter:**
- Completed is unchecked
- Time Required ≤ 15
**Sort:** Time Required (ascending)
**Properties Shown:** Task Name, Brain State, XP Value, Time Required

**Purpose:** Find quick tasks when you have limited time

---

#### View 3: 🏆 Completed Today
**Type:** Table
**Filter:**
- Completed is checked
- Completion Date is today
**Sort:** Completion Date (descending)
**Properties Shown:** Task Name, XP Value, Related Episode, Completion Date

**Purpose:** See what you accomplished today

---

### ACHIEVEMENTS DATABASE VIEWS

#### View 1: 🎖️ All Achievements
**Type:** Gallery
**Filter:** None
**Sort:** Tier (custom order: Legend, Platinum, Gold, Silver, Bronze)
**Group By:** Type
**Properties Shown:** Achievement Name, Badge Emoji, Unlocked, XP Bonus
**Card Size:** Large

**Purpose:** See all possible achievements

---

#### View 2: 🔓 Unlocked
**Type:** List
**Filter:** Unlocked is checked
**Sort:** Unlock Date (descending)
**Properties Shown:** Achievement Name, Badge Emoji, Unlock Date, XP Bonus

**Purpose:** Celebrate what you've earned

---

#### View 3: 🎯 In Progress
**Type:** Table
**Filter:** Unlocked is unchecked
**Sort:**
1. Current Progress / Target (ratio, descending)
2. XP Bonus (descending)
**Properties Shown:** Achievement Name, Current Progress, Target, Requirements, XP Bonus
**Formula Column:** Progress % = (Current Progress / Target) * 100

**Purpose:** See what you're close to unlocking

---

### WEEKLY PLANNING VIEWS

#### View 1: 📅 This Week
**Type:** Table
**Filter:** Week Of is this week
**Properties Shown:** Week Of, Goal, Planned Episodes, Status, Total XP Earned, Notes
**Limit:** 1

**Purpose:** Quick view of current week

---

#### View 2: 📈 All Weeks
**Type:** Table
**Filter:** None
**Sort:** Week Of (descending)
**Properties Shown:** Week Number, Week Of, Goal, Status, Total XP Earned, Actual Episodes

**Purpose:** Track progress over time

---

### PROGRESS LOG VIEWS

#### View 1: 📅 Calendar
**Type:** Calendar
**Calendar By:** Date
**Properties Shown:** XP Earned Today, Brain State, Mood
**Color By:** Mood

**Purpose:** Visual streak tracking

---

#### View 2: 📊 Recent Entries
**Type:** Table
**Filter:** None
**Sort:** Date (descending)
**Limit:** 30 (last 30 days)
**Properties Shown:** Date, XP Earned Today, Time Spent, Brain State, Mood, Wins

**Purpose:** Review recent progress

---

## FORMULAS & ROLLUPS

### EPISODES DATABASE

#### Formula 1: Progress %
**Name:** Progress %
**Type:** Formula
**Formula:**
```
if(prop("Status") == "Not Started", "0%",
  if(prop("Status") == "Prep", "20%",
    if(prop("Status") == "Recording", "40%",
      if(prop("Status") == "Editing", "60%",
        if(prop("Status") == "Complete", "80%",
          if(prop("Status") == "Published", "100%", "0%"))))))
```

#### Formula 2: Episode Status Emoji
**Name:** Status Emoji
**Type:** Formula
**Formula:**
```
if(prop("Status") == "Not Started", "⬜",
  if(prop("Status") == "Prep", "📝",
    if(prop("Status") == "Recording", "🎙️",
      if(prop("Status") == "Editing", "✂️",
        if(prop("Status") == "Complete", "✅",
          if(prop("Status") == "Published", "🎉", ""))))))
```

#### Formula 3: Time Variance
**Name:** Time Over/Under
**Type:** Formula
**Formula:**
```
if(empty(prop("Actual Time")), "",
  if(prop("Actual Time") > prop("Estimated Time"),
    "+" + format(prop("Actual Time") - prop("Estimated Time")) + "h over",
    format(prop("Estimated Time") - prop("Actual Time")) + "h under"))
```

#### Rollup 1: Total Tasks
**Name:** Total Tasks
**Type:** Rollup
**Relation:** Tasks
**Property:** Task Name
**Calculate:** Count all

#### Rollup 2: Completed Tasks
**Name:** Completed Tasks
**Type:** Rollup
**Relation:** Tasks
**Property:** Completed
**Calculate:** Count checked

---

### ACHIEVEMENTS DATABASE

#### Formula 1: Progress Bar
**Name:** Progress Bar
**Type:** Formula
**Formula:**
```
if(prop("Unlocked"), "✅ UNLOCKED",
  if(empty(prop("Target")), "",
    let(percent, round(prop("Current Progress") / prop("Target") * 100),
      if(percent >= 100, "🎉 Ready to Unlock!",
        if(percent >= 75, "▓▓▓▓▓▓▓░░░ " + format(percent) + "%",
          if(percent >= 50, "▓▓▓▓▓░░░░░ " + format(percent) + "%",
            if(percent >= 25, "▓▓▓░░░░░░░ " + format(percent) + "%",
              "▓░░░░░░░░░ " + format(percent) + "%")))))))
```

---

### WEEKLY PLANNING DATABASE

#### Rollup 1: Total XP This Week
**Name:** Total XP Earned
**Type:** Rollup
**Relation:** Actual Episodes
**Property:** XP Earned
**Calculate:** Sum

#### Rollup 2: Episodes Completed Count
**Name:** Episodes Completed
**Type:** Rollup
**Relation:** Actual Episodes
**Property:** Episode Title
**Calculate:** Count all

#### Formula 1: Week Summary
**Name:** Summary
**Type:** Formula
**Formula:**
```
"Week " + format(prop("Week Number")) + ": " +
format(prop("Episodes Completed")) + " episodes, " +
format(prop("Total XP Earned")) + " XP"
```

---

### PROGRESS LOG DATABASE

#### Formula 1: Productivity Score
**Name:** Productivity
**Type:** Formula
**Formula:**
```
if(prop("Brain State") == "Rest Day", "Rest",
  if(prop("XP Earned Today") >= 300, "🔥 Excellent",
    if(prop("XP Earned Today") >= 150, "✨ Great",
      if(prop("XP Earned Today") >= 50, "👍 Good",
        if(prop("XP Earned Today") > 0, "✓ Progress", "")))))
```

---

## DASHBOARD SETUP

### Create Dashboard Page: "I Want To Believe - Dashboard"

#### Section 1: Progress Overview

**Title:** 📊 OVERALL PROGRESS

**Add Linked Database:** Episodes
**View:** Table (filtered)
**Filter:** None
**Properties Shown:** Status only
**Custom View Settings:**
- Group by Status
- Show count for each group

**Add Formula Block:**
```
Total Episodes: [Count from database]
Completed: [Count where Status = Complete or Published]
Percentage: [Completed / Total * 100]%

Progress Bar:
[Create visual progress bar using emoji]
▓▓▓▓▓▓▓▓▓░░░░░░░░░░░ XX%
```

**Add Callout:**
```
🎯 Current Goal: [Pull from current week's goal]
📅 This Week: [Episode numbers from weekly planning]
```

---

#### Section 2: XP & Level System

**Title:** 🎮 LEVEL & XP

**Add Database Query:** Achievements
**Calculate Total XP:**
- Sum all Episodes.XP Earned
- Add all Achievements.XP Bonus (where Unlocked = true)

**Create Level Indicator:**
```
Current Level: [Calculate from total XP]
Current XP: [Total XP]
Next Level: [Next threshold] XP
Progress: ▓▓▓▓▓░░░░░ [XP toward next level]
```

**Level Reference:**
```
Level 1: Novice (0-500)
Level 2: Apprentice (501-1500)
Level 3: Practitioner (1501-3000)
Level 4: Professional (3001-5000)
Level 5: Expert (5001-7500)
Level 6: Master (7501-10000)
Level 7: Legend (10000+)
```

---

#### Section 3: This Week

**Title:** 📅 THIS WEEK'S FOCUS

**Add Linked Database:** Weekly Planning
**View:** This Week
**Full Page:** No

**Add Linked Database:** Episodes
**View:** In Production
**Full Page:** No

**Add Linked Database:** Tasks
**View:** By Brain State
**Limit:** Top 5 tasks
**Full Page:** No

---

#### Section 4: Quick Actions

**Title:** ⚡ QUICK ACTIONS

**Create Button Links:**
1. **🎯 Pick Next Episode** → Link to Episodes "Next Up" view
2. **📝 Add Progress** → Template for Progress Log
3. **✅ Complete Task** → Quick add to Tasks
4. **📊 Update Tracker** → Link to current episode's tracker
5. **🎉 Unlock Achievement** → Link to Achievements

---

#### Section 5: Streak & Motivation

**Title:** 🔥 STREAK TRACKER

**Add Linked Database:** Progress Log
**View:** Calendar (current month)
**Full Page:** No

**Add Callout:**
```
Current Streak: [Count consecutive days with XP > 0]
Longest Streak: [Max consecutive days]
Days This Month: [Count days with activity this month]
```

**Add Quote Block:**
```
💭 "Done is better than perfect."
💭 "Something is better than nothing."
💭 "Progress over perfection."
```

---

#### Section 6: Recent Achievements

**Title:** 🏆 RECENT UNLOCKS

**Add Linked Database:** Achievements
**View:** Unlocked
**Sort:** Unlock Date (descending)
**Limit:** 3
**Full Page:** No

---

#### Section 7: Stats & Insights

**Title:** 📈 STATISTICS

**Create Table:**
```
Episodes Completed:     [Count]
Total Recording Time:   [Sum of Actual Time]
Average Episode Time:   [Average]
Best Self-Rating:       [Max of Self Rating]
Total XP Earned:        [Sum]
Achievements Unlocked:  [Count]
Current Win Streak:     [Days]
Episodes This Month:    [Count this month]
```

---

## IMPORT INSTRUCTIONS

### Step 1: Create Databases

1. Create new Notion page: "I Want To Believe - Production System"
2. Create 5 databases (use templates below)
3. Set up all properties as specified above
4. Configure all select/multi-select options with colors

### Step 2: Import Episodes CSV

**File:** `07-TRACKING/csv-exports/episodes-import.csv`

**Steps:**
1. Open Episodes database
2. Click ⋮ menu → Merge with CSV
3. Upload `episodes-import.csv`
4. Map columns:
   - Number → Number
   - Title → Episode Title
   - Category → Category
   - Difficulty → Difficulty
   - Fun Factor → Fun Factor
   - Estimated Time → Estimated Time
5. Import all 100 rows
6. Verify import successful

**Post-Import:**
- All episodes default to Status: "Not Started"
- All checkboxes default to unchecked
- Manually add folder paths for first few episodes, then template

### Step 3: Populate Tasks Database

**Use this checklist to create task templates:**

**5-Minute Tasks (Low Energy):**
1. Read one episode brief (10 XP)
2. Update completion tracker (5 XP)
3. Browse episode list (5 XP)
4. Practice one pronunciation (10 XP)
5. Update progress visualization (5 XP)
6. Organize one folder (5 XP)
7. Check equipment (5 XP)

**15-Minute Tasks (Medium Energy):**
1. Read brief + recording notes (25 XP)
2. Mark up recording notes (15 XP)
3. Record cold open (20 XP)
4. Record outro (10 XP)
5. Edit one section (30 XP)
6. Plan next episode (15 XP)
7. Write show notes (10 XP)

**1-Hour Tasks (High Energy):**
1. Record believer section (30 XP)
2. Record skeptic section (30 XP)
3. Record your take (20 XP)
4. Complete episode edit (50 XP)
5. Record full episode (100 XP)
6. Deep research session (25 XP)
7. Batch prep 3 episodes (50 XP)

**For each task, set:**
- Task Type
- Brain State
- XP Value
- Time Required
- Repeatable = true

### Step 4: Populate Achievements

**Create all achievements from the list in DATABASE STRUCTURES section**

**For each achievement:**
- Set Type, Badge Emoji, XP Bonus
- Set Requirements
- Set Target (if applicable)
- Leave Unlocked unchecked
- Leave Current Progress at 0

### Step 5: Set Up Relations

**Episodes to Episodes:**
1. Open an episode
2. Add relation to Prerequisites (self-relation)
3. Add relation to Related Episodes (self-relation)

**Episodes to Tasks:**
1. Enable two-way relation
2. Test by linking a task to an episode

**Episodes to Weekly Planning:**
1. Enable two-way relation
2. Create first week
3. Link planned episodes

**Tasks to Progress Log:**
1. Enable two-way relation

**Episodes to Progress Log:**
1. Enable two-way relation

### Step 6: Create All Views

**For each database:**
- Create views as specified in VIEWS CONFIGURATION
- Set filters, sorts, groupings
- Configure properties shown
- Set card sizes and previews
- Test each view

### Step 7: Build Dashboard

**Follow DASHBOARD SETUP section:**
1. Create new page "Dashboard"
2. Add all sections
3. Link databases with specific views
4. Create formulas and calculations
5. Add callouts and quotes
6. Test all links

### Step 8: Create Templates

**Episode Completion Template:**
```
When episode is complete:
1. Status → Complete
2. Check all checkboxes
3. Add Actual Time
4. Add Self Rating
5. Add Notes, What Went Well, What To Improve
6. Calculate and add XP Earned
7. Link to today's Progress Log
8. Check for unlocked achievements
```

**Daily Progress Entry Template:**
```
Date: [Today]
Brain State: [Select]
Mood: [Select]
What I Did:
Wins:
Challenges:
Tomorrow's Plan:
XP Earned Today: [Calculate]
Streak Day: [Auto-calculate]
```

**Weekly Planning Template:**
```
Week Of: [Monday date]
Week Number: [Calculate]
Goal: [1 Episode / 2 Episodes / etc.]
Planned Episodes: [Link 1-2 episodes]
Prep Day: [Select]
Recording Day: [Select]
Editing Day: [Select]
Notes:
```

---

## AUTOMATION & TEMPLATES

### Notion Buttons to Create

#### Button 1: "✅ Complete Episode"
**Action:** Update episode properties
**Properties Updated:**
- Status → Complete
- Editing Date → Today
- Add entry to Progress Log
- Prompt for Self Rating
- Prompt for XP Earned

#### Button 2: "🎉 Publish Episode"
**Action:** Mark as published
**Properties Updated:**
- Status → Published
- Published Date → Today
- Check Quality Check Done
- Prompt for final notes

#### Button 3: "📝 Start Episode"
**Action:** Begin work on episode
**Properties Updated:**
- Status → Prep
- Add to this week's planning
- Create related tasks
- Mark Episode Brief Read checkbox

#### Button 4: "🎙️ Recording Done"
**Action:** Move to editing
**Properties Updated:**
- Status → Editing
- Recording Date → Today
- Recorded checkbox → true
- Prompt for Recording Time

---

## MOBILE WORKFLOW

### Mobile-Optimized Views

**For iPhone/Android Notion app:**

**Home View (Dashboard):**
- Quick stats at top
- This week's episodes
- Today's tasks
- Quick action buttons

**Episodes - Mobile View:**
- Show: Number, Title, Status, Difficulty
- Group by: Status
- Easy drag-and-drop
- Swipe to update

**Tasks - Mobile View:**
- Group by: Brain State
- Show: Task Name, XP, Time Required
- Quick checkbox
- Add button for new tasks

**Progress Log - Mobile:**
- Calendar view
- Quick daily entry button
- Recent entries list

### Mobile Quick Actions

**Create Widgets:**
1. Current episode
2. Today's XP total
3. Current streak
4. Next task to do

---

## QUICK REFERENCE

### Database Access URLs (Bookmark These)

Once set up, bookmark:
1. Dashboard
2. Episodes - Next Up view
3. Episodes - Kanban view
4. Tasks - By Brain State view
5. Progress Log - Calendar view
6. Achievements - All view

### Daily Workflow in Notion

**Morning:**
1. Open Dashboard
2. Check current week plan
3. Pick today's episode/task
4. Update Status if starting new episode

**During Work:**
1. Check tasks by brain state
2. Complete tasks, check boxes
3. Update episode progress
4. Add notes as you go

**Evening:**
1. Create Progress Log entry
2. Update episode Status
3. Calculate XP earned
4. Check for unlocked achievements
5. Plan tomorrow

**Weekly:**
1. Create new Weekly Planning entry
2. Review last week's stats
3. Plan next week's episodes
4. Update long-term goals

---

## FORMULAS CHEAT SHEET

### Useful Notion Formulas

**Calculate Days Between Dates:**
```
dateBetween(prop("End Date"), prop("Start Date"), "days")
```

**Conditional Status:**
```
if(prop("Status") == "Complete", "✅", "⬜")
```

**Percentage Calculation:**
```
round(prop("Current") / prop("Target") * 100)
```

**XP Level Calculator:**
```
if(prop("Total XP") < 500, "Level 1",
  if(prop("Total XP") < 1500, "Level 2",
    if(prop("Total XP") < 3000, "Level 3",
      if(prop("Total XP") < 5000, "Level 4",
        if(prop("Total XP") < 7500, "Level 5",
          if(prop("Total XP") < 10000, "Level 6", "Level 7"))))))
```

**Progress Bar:**
```
let(percent, round(prop("Current") / prop("Target") * 100),
  if(percent >= 100, "▓▓▓▓▓▓▓▓▓▓ 100%",
    if(percent >= 90, "▓▓▓▓▓▓▓▓▓░ " + format(percent) + "%",
      if(percent >= 80, "▓▓▓▓▓▓▓▓░░ " + format(percent) + "%",
        if(percent >= 70, "▓▓▓▓▓▓▓░░░ " + format(percent) + "%",
          if(percent >= 60, "▓▓▓▓▓▓░░░░ " + format(percent) + "%",
            if(percent >= 50, "▓▓▓▓▓░░░░░ " + format(percent) + "%",
              if(percent >= 40, "▓▓▓▓░░░░░░ " + format(percent) + "%",
                if(percent >= 30, "▓▓▓░░░░░░░ " + format(percent) + "%",
                  if(percent >= 20, "▓▓░░░░░░░░ " + format(percent) + "%",
                    if(percent >= 10, "▓░░░░░░░░░ " + format(percent) + "%",
                      "░░░░░░░░░░ " + format(percent) + "%")))))))))))
```

---

## TROUBLESHOOTING

### Common Issues

**Issue:** CSV import fails
**Solution:**
- Remove any special characters from CSV
- Ensure all required columns are present
- Import in smaller batches (25 episodes at a time)

**Issue:** Relations not working
**Solution:**
- Ensure both databases have the relation property
- Enable two-way relations
- Manually link one item to test

**Issue:** Formulas showing error
**Solution:**
- Check property names match exactly (case-sensitive)
- Ensure all referenced properties exist
- Test formula with simple values first

**Issue:** Views not filtering correctly
**Solution:**
- Check filter syntax
- Ensure property types are correct (Select vs. Text)
- Clear and re-apply filters

---

## FINAL CHECKLIST

**Before You Start Using:**
- [ ] All 5 databases created
- [ ] All properties configured
- [ ] All Select options added with colors
- [ ] CSV imported (100 episodes)
- [ ] All relations set up
- [ ] All views created (20+ views total)
- [ ] Dashboard built with all sections
- [ ] Formulas tested and working
- [ ] Templates created
- [ ] Mobile views configured
- [ ] Bookmarks saved

**Test Workflow:**
- [ ] Pick an episode from "Next Up"
- [ ] Update status to "Prep"
- [ ] Complete a task
- [ ] Add progress log entry
- [ ] Calculate XP
- [ ] Check for achievements
- [ ] Update dashboard
- [ ] Verify everything syncs

---

## ADDITIONAL RESOURCES

### Notion API Integration

**If using Notion API / connector:**

**Endpoints you'll need:**
- Create database
- Create page (in database)
- Update page properties
- Query database
- Get page

**Sample API calls in documentation.**

**Environment Variables:**
- NOTION_API_KEY
- DATABASE_ID_EPISODES
- DATABASE_ID_TASKS
- DATABASE_ID_ACHIEVEMENTS
- DATABASE_ID_WEEKLY
- DATABASE_ID_PROGRESS

---

## CONCLUSION

**This system gives you:**
- ✅ Complete visual tracking of all 100 episodes
- ✅ XP and leveling gamification
- ✅ Brain-state-based task management
- ✅ Progress visualization and motivation
- ✅ Mobile-friendly workflow
- ✅ Flexible planning system
- ✅ Achievement tracking

**The result:**
A fully functional ADHD-optimized podcast production system in Notion that syncs with your file repository and helps you actually record 100 episodes.

---

**NEXT STEPS:**

1. Save this guide
2. Open Notion
3. Start with creating the Episodes database
4. Import the CSV
5. Build from there
6. Celebrate your setup!

**YOU'VE GOT THIS. NOW GO BUILD IT.**

🎙️ **LEGENDARY STATUS AWAITS** 🎙️
