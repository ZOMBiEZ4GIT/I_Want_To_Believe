# NOTION INTEGRATION GUIDE
## Import Your Episodes Into Notion for Visual Tracking

**Turn this repository into a beautiful Notion database with progress tracking.**

---

## WHY NOTION?

**Benefits:**
- Visual kanban boards (drag episodes through stages)
- Progress bars and percentages
- Calendar view for scheduling
- Mobile access
- Satisfying to update
- Dopamine hits from moving cards

---

## DATABASE STRUCTURE

### Create a New Database

**In Notion:**
1. Create new page: "I Want To Believe - Production"
2. Add database: "Episodes"
3. Add these properties:

### Required Properties

| Property Name | Type | Options/Format |
|---------------|------|----------------|
| Episode Title | Title | (default) |
| Number | Number | Format: 001, 002, etc. |
| Status | Select | Not Started, Prep, Recording, Editing, Complete, Published |
| Category | Select | UFO Sighting, Abduction, Ancient Mystery, Government, X-Files, etc. |
| Difficulty | Select | ⭐, ⭐⭐⭐, ⭐⭐⭐⭐⭐ |
| Fun Factor | Select | 🎉, 🎉🎉🎉, 🎉🎉🎉🎉🎉 |
| Recording Date | Date | When you recorded it |
| Published Date | Date | When you published it |
| Time Spent | Number | Total hours (prep + record + edit) |
| XP Earned | Number | Track your XP |
| Self Rating | Select | ⭐⭐⭐⭐⭐ (1-5 stars) |
| Files | Files & Media | Upload MP3 when done |
| Notes | Text | Your thoughts, lessons learned |

### Optional Properties

| Property Name | Type | Purpose |
|---------------|------|---------|
| Estimated Time | Number | How long you think it'll take |
| Week Planned | Date | Planning ahead |
| Priority | Select | High, Medium, Low |
| Prerequisites | Relation | Link to other episodes to listen first |
| Related Episodes | Relation | Thematically connected |

---

## VIEW CONFIGURATIONS

### View 1: Board (Kanban)

**Group by:** Status
**Columns:**
- Not Started
- Prep
- Recording
- Editing
- Complete
- Published

**Drag episodes through workflow!**

**Filters:**
- None (show all)

**Sort:**
- By Number (ascending)

---

### View 2: Table (All Details)

**Show all properties**
**Sort:** By Number
**Use for:** Detailed tracking

---

### View 3: Calendar

**Calendar by:** Recording Date
**Use for:** Planning when to record
**Color by:** Status

---

### View 4: Gallery

**Show:** Episode artwork (if you create it)
**Group by:** Status
**Use for:** Visual satisfaction

---

### View 5: Next Up

**Filter:**
- Status = "Not Started"
- Difficulty = ⭐ or ⭐⭐⭐

**Sort:** By Fun Factor (descending)

**Limit:** First 5 items

**Use for:** Quick episode selection

---

## DASHBOARD SETUP

### Create Dashboard Page

**Add:**

**1. Progress Ring:**
```
Episodes Complete: X/100
Percentage: X%
```

**2. Level & XP:**
```
Current Level: [X]
Current XP: [XXXX]
Next Level: [XXXX XP needed]
```

**3. This Week:**
```
Planned: [Episode X]
Status: [Recording/Editing/etc]
```

**4. Streak:**
```
Current Streak: [X days]
Longest Streak: [X days]
```

**5. Quick Stats:**
```
Episodes This Month: [X]
Total Time Spent: [XX hours]
Average Episode Time: [X hours]
```

---

## CSV IMPORT

### Import Episodes

**File:** `07-TRACKING/csv-exports/episodes-import.csv`

**Steps:**
1. Open Notion database
2. Click "..." menu → Import → CSV
3. Select `episodes-import.csv`
4. Map columns to properties
5. Import!

**All 100 episodes will populate your database!**

---

## WORKFLOW IN NOTION

### When Starting Episode:

1. Open database
2. Find episode (or use "Next Up" view)
3. Click to open
4. Change Status → "Prep"
5. Add Recording Date (planned)
6. Add any prep notes

### While Recording:

1. Update Status → "Recording"
2. Add notes about session
3. Track time spent

### While Editing:

1. Update Status → "Editing"
2. Upload rough audio file
3. Track editing time

### When Complete:

1. Update Status → "Complete"
2. Upload final MP3
3. Log total time
4. Add self-rating
5. Calculate and enter XP earned
6. Write lessons learned

### When Published:

1. Update Status → "Published"
2. Add published date
3. CELEBRATE!
4. Look at progress percentage increase

---

## MOBILE WORKFLOW

**Notion mobile app:**
- Quick status updates
- Check next episodes to record
- Update on-the-go
- Satisfying to drag cards

**Great for:**
- Post-recording updates
- Tracking ideas
- Maintaining streaks
- Visual progress checks

---

## FORMULAS & AUTOMATION

### Progress Percentage

**Formula:**
```
prop("Status") == "Published" ? 1 : 0
```

**Rollup:**
Sum of all "Published" episodes / 100 = %

### Time Tracking

**Formula for Average:**
```
Total Time Spent (sum) / Episodes Complete (count)
```

### XP Tracking

**Formula for Total XP:**
```
Sum of all "XP Earned" property
```

---

## TIPS FOR ADHD-FRIENDLY NOTION USE

**DO:**
- Update immediately after sessions
- Use kanban view (visual, satisfying)
- Check off progress
- Keep it simple

**DON'T:**
- Over-customize (productive procrastination)
- Create too many views
- Make it overwhelming
- Spend more time in Notion than recording

**Balance:** Notion should motivate, not distract

---

## ALTERNATIVE: SIMPLE SPREADSHEET

**Don't want Notion?**

Use: `07-TRACKING/csv-exports/episodes-import.csv` in:
- Google Sheets
- Excel
- Numbers (Mac)

**Still get:**
- Progress tracking
- XP calculation
- Status updates
- Visual satisfaction

---

## REWARD: NOTION TEMPLATE

**After Episode 25:**

Consider upgrading to:
- Custom dashboard
- Advanced formulas
- Linked databases
- Fancy visualizations

**But start simple. Add complexity only if it helps.**

---

**IMPORT THE CSV, START DRAGGING CARDS, FEEL PRODUCTIVE.**
