# NOTION API INTEGRATION GUIDE
## Automate Setup with Notion Connector or API

**For users who want to programmatically set up the Notion workspace or integrate with automation tools.**

---

## OVERVIEW

This guide provides:
- Notion API setup instructions
- Database schema in JSON format
- Sample API calls for automation
- Integration with Zapier/Make/n8n
- Sync scripts for keeping Notion updated

---

## PREREQUISITES

### 1. Create Notion Integration

**Steps:**
1. Go to https://www.notion.so/my-integrations
2. Click "+ New integration"
3. Name: "I Want To Believe Podcast System"
4. Select workspace
5. Set capabilities:
   - ✅ Read content
   - ✅ Update content
   - ✅ Insert content
6. Click "Submit"
7. **Copy the Internal Integration Token** (keep secret!)

### 2. Share Databases with Integration

**For each database you create:**
1. Open the database page
2. Click "•••" (top right)
3. Click "Add connections"
4. Select your integration
5. Click "Confirm"

---

## ENVIRONMENT SETUP

### Environment Variables

```bash
# .env file
NOTION_API_KEY=secret_xxxxxxxxxxxxxxxxxxxx
NOTION_VERSION=2022-06-28

# Database IDs (you'll get these after creating)
NOTION_DB_EPISODES=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
NOTION_DB_TASKS=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
NOTION_DB_ACHIEVEMENTS=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
NOTION_DB_WEEKLY=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
NOTION_DB_PROGRESS=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

---

## DATABASE SCHEMAS (JSON)

### Episodes Database Schema

```json
{
  "parent": {
    "type": "page_id",
    "page_id": "YOUR_PARENT_PAGE_ID"
  },
  "title": [
    {
      "type": "text",
      "text": {
        "content": "📺 Episodes"
      }
    }
  ],
  "properties": {
    "Episode Title": {
      "title": {}
    },
    "Number": {
      "number": {
        "format": "number"
      }
    },
    "Status": {
      "select": {
        "options": [
          {"name": "Not Started", "color": "gray"},
          {"name": "Prep", "color": "yellow"},
          {"name": "Recording", "color": "orange"},
          {"name": "Editing", "color": "blue"},
          {"name": "Complete", "color": "green"},
          {"name": "Published", "color": "purple"}
        ]
      }
    },
    "Category": {
      "multi_select": {
        "options": [
          {"name": "UFO Sighting", "color": "red"},
          {"name": "Abduction", "color": "orange"},
          {"name": "Ancient Mystery", "color": "yellow"},
          {"name": "Government", "color": "blue"},
          {"name": "X-Files", "color": "purple"},
          {"name": "UAP/Modern", "color": "green"},
          {"name": "Physical Evidence", "color": "brown"},
          {"name": "Whistleblower", "color": "pink"},
          {"name": "Media/Culture", "color": "gray"},
          {"name": "Documents/Hoax", "color": "red"}
        ]
      }
    },
    "Difficulty": {
      "select": {
        "options": [
          {"name": "⭐", "color": "green"},
          {"name": "⭐⭐", "color": "blue"},
          {"name": "⭐⭐⭐", "color": "yellow"},
          {"name": "⭐⭐⭐⭐", "color": "orange"},
          {"name": "⭐⭐⭐⭐⭐", "color": "red"}
        ]
      }
    },
    "Fun Factor": {
      "select": {
        "options": [
          {"name": "🎉", "color": "gray"},
          {"name": "🎉🎉", "color": "blue"},
          {"name": "🎉🎉🎉", "color": "green"},
          {"name": "🎉🎉🎉🎉", "color": "yellow"},
          {"name": "🎉🎉🎉🎉🎉", "color": "red"}
        ]
      }
    },
    "Estimated Time": {
      "number": {
        "format": "number"
      }
    },
    "Actual Time": {
      "number": {
        "format": "number"
      }
    },
    "Recording Date": {
      "date": {}
    },
    "Editing Date": {
      "date": {}
    },
    "Published Date": {
      "date": {}
    },
    "XP Earned": {
      "number": {
        "format": "number"
      }
    },
    "Self Rating": {
      "select": {
        "options": [
          {"name": "⭐", "color": "gray"},
          {"name": "⭐⭐", "color": "blue"},
          {"name": "⭐⭐⭐", "color": "green"},
          {"name": "⭐⭐⭐⭐", "color": "yellow"},
          {"name": "⭐⭐⭐⭐⭐", "color": "red"}
        ]
      }
    },
    "Audio File": {
      "files": {}
    },
    "Episode Brief Read": {
      "checkbox": {}
    },
    "Framework Read": {
      "checkbox": {}
    },
    "Recording Notes Marked": {
      "checkbox": {}
    },
    "Recorded": {
      "checkbox": {}
    },
    "Edited": {
      "checkbox": {}
    },
    "Quality Check Done": {
      "checkbox": {}
    },
    "Notes": {
      "rich_text": {}
    },
    "What Went Well": {
      "rich_text": {}
    },
    "What To Improve": {
      "rich_text": {}
    },
    "Folder Path": {
      "rich_text": {}
    },
    "Brief Path": {
      "rich_text": {}
    },
    "Framework Path": {
      "rich_text": {}
    },
    "Recording Notes Path": {
      "rich_text": {}
    },
    "Tracker Path": {
      "rich_text": {}
    }
  }
}
```

### Tasks Database Schema

```json
{
  "parent": {
    "type": "page_id",
    "page_id": "YOUR_PARENT_PAGE_ID"
  },
  "title": [
    {
      "type": "text",
      "text": {
        "content": "✅ Tasks"
      }
    }
  ],
  "properties": {
    "Task Name": {
      "title": {}
    },
    "Task Type": {
      "select": {
        "options": [
          {"name": "5-Minute", "color": "green"},
          {"name": "15-Minute", "color": "blue"},
          {"name": "1-Hour", "color": "orange"},
          {"name": "Learning", "color": "purple"},
          {"name": "Recording", "color": "red"},
          {"name": "Editing", "color": "yellow"},
          {"name": "Publishing", "color": "pink"},
          {"name": "Planning", "color": "gray"},
          {"name": "Admin", "color": "brown"}
        ]
      }
    },
    "Brain State": {
      "select": {
        "options": [
          {"name": "High Energy", "color": "red"},
          {"name": "Medium Energy", "color": "yellow"},
          {"name": "Low Energy", "color": "blue"},
          {"name": "Zero Focus", "color": "gray"}
        ]
      }
    },
    "XP Value": {
      "number": {
        "format": "number"
      }
    },
    "Time Required": {
      "number": {
        "format": "number"
      }
    },
    "Category": {
      "select": {
        "options": [
          {"name": "Prep", "color": "yellow"},
          {"name": "Production", "color": "red"},
          {"name": "Post-Production", "color": "blue"},
          {"name": "Admin", "color": "gray"},
          {"name": "Skill-Building", "color": "purple"},
          {"name": "Planning", "color": "green"}
        ]
      }
    },
    "Completed": {
      "checkbox": {}
    },
    "Completion Date": {
      "date": {}
    },
    "Description": {
      "rich_text": {}
    },
    "Difficulty": {
      "select": {
        "options": [
          {"name": "Easy", "color": "green"},
          {"name": "Medium", "color": "yellow"},
          {"name": "Hard", "color": "red"}
        ]
      }
    },
    "Repeatable": {
      "checkbox": {}
    }
  }
}
```

### Achievements Database Schema

```json
{
  "parent": {
    "type": "page_id",
    "page_id": "YOUR_PARENT_PAGE_ID"
  },
  "title": [
    {
      "type": "text",
      "text": {
        "content": "🏆 Achievements"
      }
    }
  ],
  "properties": {
    "Achievement Name": {
      "title": {}
    },
    "Type": {
      "select": {
        "options": [
          {"name": "Milestone", "color": "yellow"},
          {"name": "Skill", "color": "blue"},
          {"name": "Streak", "color": "red"},
          {"name": "Quality", "color": "green"},
          {"name": "Comeback", "color": "purple"},
          {"name": "Special", "color": "pink"}
        ]
      }
    },
    "Badge Emoji": {
      "rich_text": {}
    },
    "XP Bonus": {
      "number": {
        "format": "number"
      }
    },
    "Unlocked": {
      "checkbox": {}
    },
    "Unlock Date": {
      "date": {}
    },
    "Requirements": {
      "rich_text": {}
    },
    "Description": {
      "rich_text": {}
    },
    "Tier": {
      "select": {
        "options": [
          {"name": "Bronze", "color": "brown"},
          {"name": "Silver", "color": "gray"},
          {"name": "Gold", "color": "yellow"},
          {"name": "Platinum", "color": "blue"},
          {"name": "Legend", "color": "purple"}
        ]
      }
    },
    "Current Progress": {
      "number": {
        "format": "number"
      }
    },
    "Target": {
      "number": {
        "format": "number"
      }
    }
  }
}
```

---

## SAMPLE API CALLS

### Create Episode Entry

```javascript
// Node.js example using @notionhq/client

const { Client } = require('@notionhq/client');

const notion = new Client({ auth: process.env.NOTION_API_KEY });

async function createEpisode(episodeData) {
  const response = await notion.pages.create({
    parent: {
      database_id: process.env.NOTION_DB_EPISODES
    },
    properties: {
      'Episode Title': {
        title: [
          {
            text: {
              content: episodeData.title
            }
          }
        ]
      },
      'Number': {
        number: episodeData.number
      },
      'Status': {
        select: {
          name: 'Not Started'
        }
      },
      'Category': {
        multi_select: episodeData.categories.map(cat => ({ name: cat }))
      },
      'Difficulty': {
        select: {
          name: episodeData.difficulty
        }
      },
      'Fun Factor': {
        select: {
          name: episodeData.funFactor
        }
      },
      'Estimated Time': {
        number: episodeData.estimatedTime
      },
      'Folder Path': {
        rich_text: [
          {
            text: {
              content: `03-EPISODES/episode-${String(episodeData.number).padStart(3, '0')}-${episodeData.slug}/`
            }
          }
        ]
      }
    }
  });

  return response;
}

// Example usage
createEpisode({
  title: 'The Roswell Incident',
  number: 1,
  categories: ['UFO Crash', 'Government'],
  difficulty: '⭐⭐⭐⭐⭐',
  funFactor: '🎉🎉🎉🎉🎉',
  estimatedTime: 6,
  slug: 'the-roswell-incident'
});
```

### Update Episode Status

```javascript
async function updateEpisodeStatus(pageId, newStatus) {
  const response = await notion.pages.update({
    page_id: pageId,
    properties: {
      'Status': {
        select: {
          name: newStatus
        }
      }
    }
  });

  return response;
}

// Update to "Recording"
updateEpisodeStatus('page-id-here', 'Recording');
```

### Query Episodes by Status

```javascript
async function getEpisodesByStatus(status) {
  const response = await notion.databases.query({
    database_id: process.env.NOTION_DB_EPISODES,
    filter: {
      property: 'Status',
      select: {
        equals: status
      }
    },
    sorts: [
      {
        property: 'Number',
        direction: 'ascending'
      }
    ]
  });

  return response.results;
}

// Get all episodes in "Recording" status
const recordingEpisodes = await getEpisodesByStatus('Recording');
```

### Bulk Import from CSV

```javascript
const fs = require('fs');
const csv = require('csv-parser');

async function importEpisodesFromCSV(csvFilePath) {
  const episodes = [];

  fs.createReadStream(csvFilePath)
    .pipe(csv())
    .on('data', (row) => {
      episodes.push(row);
    })
    .on('end', async () => {
      console.log(`Importing ${episodes.length} episodes...`);

      for (const episode of episodes) {
        await createEpisode({
          title: episode.Title,
          number: parseInt(episode.Number),
          categories: episode.Category.split(',').map(c => c.trim()),
          difficulty: episode.Difficulty,
          funFactor: episode['Fun Factor'],
          estimatedTime: parseFloat(episode['Estimated Time']),
          slug: episode.Title.toLowerCase().replace(/[^a-z0-9]+/g, '-')
        });

        console.log(`✓ Imported Episode ${episode.Number}`);
      }

      console.log('Import complete!');
    });
}

// Import from CSV
importEpisodesFromCSV('07-TRACKING/csv-exports/episodes-import.csv');
```

### Calculate Total XP

```javascript
async function calculateTotalXP() {
  const episodes = await notion.databases.query({
    database_id: process.env.NOTION_DB_EPISODES,
    filter: {
      property: 'Status',
      select: {
        equals: 'Published'
      }
    }
  });

  let totalXP = 0;

  for (const episode of episodes.results) {
    const xpEarned = episode.properties['XP Earned'].number || 0;
    totalXP += xpEarned;
  }

  const achievements = await notion.databases.query({
    database_id: process.env.NOTION_DB_ACHIEVEMENTS,
    filter: {
      property: 'Unlocked',
      checkbox: {
        equals: true
      }
    }
  });

  for (const achievement of achievements.results) {
    const bonusXP = achievement.properties['XP Bonus'].number || 0;
    totalXP += bonusXP;
  }

  return totalXP;
}

// Get current level
async function getCurrentLevel() {
  const totalXP = await calculateTotalXP();

  if (totalXP < 500) return { level: 1, name: 'Novice', xp: totalXP, next: 500 };
  if (totalXP < 1500) return { level: 2, name: 'Apprentice', xp: totalXP, next: 1500 };
  if (totalXP < 3000) return { level: 3, name: 'Practitioner', xp: totalXP, next: 3000 };
  if (totalXP < 5000) return { level: 4, name: 'Professional', xp: totalXP, next: 5000 };
  if (totalXP < 7500) return { level: 5, name: 'Expert', xp: totalXP, next: 7500 };
  if (totalXP < 10000) return { level: 6, name: 'Master', xp: totalXP, next: 10000 };
  return { level: 7, name: 'Legend', xp: totalXP, next: null };
}
```

### Check for Unlocked Achievements

```javascript
async function checkAchievements() {
  const completedEpisodes = await notion.databases.query({
    database_id: process.env.NOTION_DB_EPISODES,
    filter: {
      or: [
        { property: 'Status', select: { equals: 'Complete' } },
        { property: 'Status', select: { equals: 'Published' } }
      ]
    }
  });

  const completedCount = completedEpisodes.results.length;

  const achievements = await notion.databases.query({
    database_id: process.env.NOTION_DB_ACHIEVEMENTS,
    filter: {
      property: 'Unlocked',
      checkbox: {
        equals: false
      }
    }
  });

  const newUnlocks = [];

  for (const achievement of achievements.results) {
    const target = achievement.properties.Target?.number;
    const type = achievement.properties.Type?.select?.name;

    if (type === 'Milestone' && completedCount >= target) {
      await notion.pages.update({
        page_id: achievement.id,
        properties: {
          'Unlocked': { checkbox: true },
          'Unlock Date': { date: { start: new Date().toISOString() } },
          'Current Progress': { number: completedCount }
        }
      });

      newUnlocks.push(achievement.properties['Achievement Name'].title[0].text.content);
    }
  }

  return newUnlocks;
}
```

---

## AUTOMATION WORKFLOWS

### Zapier Integration

**Trigger:** New row in Google Sheets
**Action:** Create Notion database item

**Setup:**
1. Create Zap
2. Trigger: Google Sheets - New Row
3. Action: Notion - Create Database Item
4. Map fields:
   - Title → Episode Title
   - Number → Number
   - Status → Not Started (default)
   - Etc.

### Make.com (Integromat) Scenario

**Module 1:** Watch CSV file
**Module 2:** Iterator (loop through rows)
**Module 3:** Notion - Create Database Item
**Module 4:** Notion - Update Page (add relations)

### n8n Workflow

```json
{
  "nodes": [
    {
      "type": "n8n-nodes-base.httpRequest",
      "name": "Create Episode",
      "parameters": {
        "url": "https://api.notion.com/v1/pages",
        "method": "POST",
        "bodyParametersJson": "={{JSON.stringify({\n  parent: { database_id: $env.NOTION_DB_EPISODES },\n  properties: {\n    'Episode Title': {\n      title: [{ text: { content: $json.title } }]\n    },\n    'Number': { number: $json.number },\n    'Status': { select: { name: 'Not Started' } }\n  }\n})}}",
        "options": {
          "headers": {
            "Authorization": "Bearer {{$env.NOTION_API_KEY}}",
            "Notion-Version": "2022-06-28",
            "Content-Type": "application/json"
          }
        }
      }
    }
  ]
}
```

---

## SYNC SCRIPTS

### Sync File System to Notion

```javascript
const fs = require('fs');
const path = require('path');

async function syncEpisodeFiles() {
  const episodesDir = '03-EPISODES';
  const folders = fs.readdirSync(episodesDir);

  for (const folder of folders) {
    const match = folder.match(/episode-(\d+)-(.*)/);
    if (!match) continue;

    const number = parseInt(match[1]);
    const slug = match[2];

    const folderPath = path.join(episodesDir, folder);
    const files = fs.readdirSync(folderPath);

    const hasEpisodeBrief = files.includes('EPISODE-BRIEF.md');
    const hasFramework = files.includes('FULL-FRAMEWORK.md');
    const hasRecordingNotes = files.includes('RECORDING-NOTES.md');
    const hasTracker = files.includes('COMPLETION-TRACKER.md');

    // Find corresponding Notion page
    const pages = await notion.databases.query({
      database_id: process.env.NOTION_DB_EPISODES,
      filter: {
        property: 'Number',
        number: {
          equals: number
        }
      }
    });

    if (pages.results.length > 0) {
      const pageId = pages.results[0].id;

      // Update file existence
      await notion.pages.update({
        page_id: pageId,
        properties: {
          'Episode Brief Read': { checkbox: hasEpisodeBrief },
          'Framework Read': { checkbox: hasFramework },
          'Recording Notes Marked': { checkbox: hasRecordingNotes }
        }
      });

      console.log(`✓ Synced Episode ${number}`);
    }
  }
}
```

### Watch for File Changes

```javascript
const chokidar = require('chokidar');

const watcher = chokidar.watch('03-EPISODES/**/COMPLETION-TRACKER.md', {
  persistent: true
});

watcher.on('change', async (filepath) => {
  console.log(`File ${filepath} changed`);

  const match = filepath.match(/episode-(\d+)/);
  if (!match) return;

  const number = parseInt(match[1]);

  // Read the tracker file and parse status
  const content = fs.readFileSync(filepath, 'utf8');

  const status = parseStatus(content); // Your parsing logic
  const xpEarned = parseXP(content);

  // Update Notion
  const pages = await notion.databases.query({
    database_id: process.env.NOTION_DB_EPISODES,
    filter: {
      property: 'Number',
      number: { equals: number }
    }
  });

  if (pages.results.length > 0) {
    await notion.pages.update({
      page_id: pages.results[0].id,
      properties: {
        'Status': { select: { name: status } },
        'XP Earned': { number: xpEarned }
      }
    });

    console.log(`✓ Updated Episode ${number} in Notion`);
  }
});
```

---

## WEBHOOK INTEGRATION

### Receive Notion Updates

```javascript
const express = require('express');
const app = express();

app.use(express.json());

app.post('/notion-webhook', async (req, res) => {
  const event = req.body;

  if (event.type === 'page.updated') {
    const pageId = event.page.id;

    // Get full page data
    const page = await notion.pages.retrieve({ page_id: pageId });

    // Check if it's an episode
    if (page.parent.database_id === process.env.NOTION_DB_EPISODES) {
      const status = page.properties.Status?.select?.name;

      if (status === 'Published') {
        // Check achievements
        const newUnlocks = await checkAchievements();

        if (newUnlocks.length > 0) {
          console.log(`🎉 Unlocked: ${newUnlocks.join(', ')}`);
          // Send notification, update dashboard, etc.
        }
      }
    }
  }

  res.status(200).send('OK');
});

app.listen(3000, () => {
  console.log('Webhook server running on port 3000');
});
```

---

## HELPER FUNCTIONS

### Parse Markdown Files

```javascript
const matter = require('gray-matter');

function parseEpisodeBrief(filepath) {
  const content = fs.readFileSync(filepath, 'utf8');
  const parsed = matter(content);

  return {
    title: parsed.data.title || extractTitleFromContent(parsed.content),
    difficulty: extractDifficulty(parsed.content),
    funFactor: extractFunFactor(parsed.content),
    recordingTime: extractRecordingTime(parsed.content),
    relatedEpisodes: extractRelatedEpisodes(parsed.content)
  };
}

function extractDifficulty(content) {
  const match = content.match(/Difficulty:\s*(⭐+)/);
  return match ? match[1] : '⭐⭐⭐';
}

function extractFunFactor(content) {
  const match = content.match(/Fun Factor:\s*(🎉+)/);
  return match ? match[1] : '🎉🎉🎉';
}
```

### Generate Dashboard Data

```javascript
async function generateDashboardData() {
  const episodes = await notion.databases.query({
    database_id: process.env.NOTION_DB_EPISODES
  });

  const stats = {
    total: episodes.results.length,
    notStarted: 0,
    prep: 0,
    recording: 0,
    editing: 0,
    complete: 0,
    published: 0
  };

  for (const episode of episodes.results) {
    const status = episode.properties.Status?.select?.name || 'Not Started';
    const key = status.toLowerCase().replace(' ', '');
    if (stats.hasOwnProperty(key)) {
      stats[key]++;
    } else {
      stats.notStarted++;
    }
  }

  stats.percentComplete = Math.round((stats.published / stats.total) * 100);

  const level = await getCurrentLevel();

  return {
    stats,
    level,
    progressBar: generateProgressBar(stats.percentComplete)
  };
}

function generateProgressBar(percent) {
  const filled = Math.floor(percent / 10);
  const empty = 10 - filled;
  return '▓'.repeat(filled) + '░'.repeat(empty) + ' ' + percent + '%';
}
```

---

## TESTING

### Test Database Creation

```javascript
async function testSetup() {
  try {
    // Test creating episode
    const testEpisode = await createEpisode({
      title: 'TEST EPISODE',
      number: 999,
      categories: ['Test'],
      difficulty: '⭐',
      funFactor: '🎉',
      estimatedTime: 1,
      slug: 'test-episode'
    });

    console.log('✓ Episode creation works');

    // Test updating episode
    await updateEpisodeStatus(testEpisode.id, 'Prep');
    console.log('✓ Episode update works');

    // Test querying
    const episodes = await getEpisodesByStatus('Prep');
    console.log(`✓ Query works (found ${episodes.length} episodes)`);

    // Clean up test episode
    await notion.pages.update({
      page_id: testEpisode.id,
      archived: true
    });

    console.log('✓ All tests passed!');
  } catch (error) {
    console.error('✗ Test failed:', error);
  }
}

testSetup();
```

---

## BEST PRACTICES

### Rate Limiting

Notion API has rate limits:
- 3 requests per second
- Implement exponential backoff

```javascript
async function rateLimitedRequest(fn, retries = 3) {
  for (let i = 0; i < retries; i++) {
    try {
      return await fn();
    } catch (error) {
      if (error.code === 'rate_limited' && i < retries - 1) {
        const delay = Math.pow(2, i) * 1000;
        console.log(`Rate limited, waiting ${delay}ms...`);
        await new Promise(resolve => setTimeout(resolve, delay));
      } else {
        throw error;
      }
    }
  }
}
```

### Error Handling

```javascript
async function safeNotionCall(fn, fallback = null) {
  try {
    return await fn();
  } catch (error) {
    console.error('Notion API Error:', error.message);

    if (error.code === 'object_not_found') {
      console.log('Object not found, returning fallback');
      return fallback;
    }

    if (error.code === 'validation_error') {
      console.error('Validation error:', error.message);
    }

    throw error;
  }
}
```

### Batch Operations

```javascript
async function batchCreateEpisodes(episodes) {
  const batchSize = 10;
  const batches = [];

  for (let i = 0; i < episodes.length; i += batchSize) {
    batches.push(episodes.slice(i, i + batchSize));
  }

  for (const batch of batches) {
    await Promise.all(batch.map(ep =>
      rateLimitedRequest(() => createEpisode(ep))
    ));

    console.log(`✓ Batch complete (${batch.length} episodes)`);

    // Rate limit: wait 1 second between batches
    await new Promise(resolve => setTimeout(resolve, 1000));
  }
}
```

---

## COMPLETE SETUP SCRIPT

```javascript
#!/usr/bin/env node

const { Client } = require('@notionhq/client');
const fs = require('fs');
const csv = require('csv-parser');

const notion = new Client({ auth: process.env.NOTION_API_KEY });

async function setupCompleteSystem() {
  console.log('🚀 Starting Notion setup...\n');

  // Step 1: Create databases
  console.log('1. Creating databases...');
  const episodesDb = await createDatabase('Episodes', episodesSchema);
  const tasksDb = await createDatabase('Tasks', tasksSchema);
  const achievementsDb = await createDatabase('Achievements', achievementsSchema);
  console.log('✓ Databases created\n');

  // Step 2: Import episodes
  console.log('2. Importing episodes...');
  await importCSV('episodes-import.csv', episodesDb.id, parseEpisodeRow);
  console.log('✓ Episodes imported\n');

  // Step 3: Import tasks
  console.log('3. Importing tasks...');
  await importCSV('tasks-template.csv', tasksDb.id, parseTaskRow);
  console.log('✓ Tasks imported\n');

  // Step 4: Import achievements
  console.log('4. Importing achievements...');
  await importCSV('achievements-import.csv', achievementsDb.id, parseAchievementRow);
  console.log('✓ Achievements imported\n');

  // Step 5: Create relations
  console.log('5. Setting up relations...');
  await setupRelations(episodesDb.id, tasksDb.id);
  console.log('✓ Relations configured\n');

  console.log('🎉 Setup complete!');
  console.log('\nDatabase IDs:');
  console.log(`NOTION_DB_EPISODES=${episodesDb.id}`);
  console.log(`NOTION_DB_TASKS=${tasksDb.id}`);
  console.log(`NOTION_DB_ACHIEVEMENTS=${achievementsDb.id}`);
}

setupCompleteSystem().catch(console.error);
```

---

## TROUBLESHOOTING

### Common Issues

**Issue:** 401 Unauthorized
**Solution:** Check API key, ensure integration has access

**Issue:** 404 Database not found
**Solution:** Share database with integration

**Issue:** 400 Validation error
**Solution:** Check property names match exactly (case-sensitive)

**Issue:** Rate limited
**Solution:** Implement backoff, reduce request frequency

---

## NEXT STEPS

1. **Set up API key**
2. **Run test script**
3. **Import episodes CSV**
4. **Configure automation**
5. **Build dashboard**
6. **Start recording!**

---

**YOU NOW HAVE COMPLETE PROGRAMMATIC CONTROL OF YOUR NOTION WORKSPACE.**

🎙️ **AUTOMATE AND CONQUER** 🎙️
