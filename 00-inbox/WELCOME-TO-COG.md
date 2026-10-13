---
type: guide
created: 2026-09-21
tags: ["#welcome", "#getting-started", "#cog"]
---

# Welcome to Your COG Second Brain, Arjun!

Your COG is now personalized and ready to use. Here's how to get started:

## Your Profile Documents

I've created these documents to store your preferences:

- **[[MY-PROFILE]]** - Your basic info, role pack, and workflow preferences
- **[[MY-INTERESTS]]** - Topics for your daily briefs
- **[[MY-INTEGRATIONS]]** - Your active and disabled integrations

**You can edit these files anytime.** COG reads them when you use skills, so your changes take effect immediately.

## Skills for Your Role

Your role (Business Analyst on a data platform migration) didn't map to one of the built-in role packs, so here are COG's core skills, ordered for what you described — structuring meetings/stakeholder info, and building data/ML skill:

1. **meeting-transcript** — Turn stakeholder meeting recordings/notes into structured decisions, action items, and owners. This is your main tool for the migration project.
2. **braindump** — Quick capture for things you're learning on the new data platform, Power BI notes, or half-formed ideas from meetings — auto-classified into the right project/domain.
3. **knowledge-consolidation** — Once you've got enough scattered notes (meeting notes, platform-learning braindumps), build them into consolidated frameworks — e.g. "what stakeholders actually want from the new platform."
4. **daily-brief** — Personalized news/intelligence on your topics (data platforms, ML, Power BI).
5. **url-dump** — Save docs/tutorials/blog posts on the new platform or ML topics with auto-extracted takeaways.
6. **weekly-checkin** — Weekly pattern analysis across your notes.
7. **update-cog** — Keep the COG framework current.

Since you set **Agent team mode**, these skills will delegate research/data-collection/writing to specialist sub-agents (per `.claude/agents/`) for deeper results where useful, rather than handling everything in the main conversation.

## Your Integrations

**Active**: GitHub / Jira / Linear, Slack / Teams, Power BI
**Disabled**: ElevenLabs

You can change these anytime by editing [[MY-INTEGRATIONS]].

## Quick Start

### 1. Daily Morning Routine
Invoke the daily-brief skill to get your personalized intelligence briefing covering: data platform migration, business analysis practice, data analytics/engineering, machine learning, Power BI.

### 2. Capture Your Thoughts
Use the braindump skill to quickly capture ideas, insights, and thoughts. Your braindumps will automatically be categorized into your professional and project domains.

Choose from your active projects:
- [[04-projects/data-platform-migration/PROJECT-OVERVIEW|Data Platform Migration]]

### 3. Weekly Reflection
Every week, use the weekly-checkin skill to review your week's insights and patterns.

## Your Active Projects

You're tracking:
- [[04-projects/data-platform-migration/PROJECT-OVERVIEW|Data Platform Migration]]

When you use the braindump skill, select this project to automatically file your thoughts in the right place. Use meeting-transcript right after stakeholder meetings to keep this project's decision log current.

## How COG Uses Your Profile

**Daily Briefs**: Uses [[MY-INTERESTS]] to curate relevant news
**Braindumps**: Offers your projects from [[MY-PROFILE]] as options
**Weekly Check-ins**: Reviews progress across your domains

## Next Steps

1. **Try your first braindump**: Use the braindump skill and start writing
2. **Get your daily brief**: Invoke the daily-brief skill to see curated intelligence
3. **Explore your vault**: All your files are organized in the sidebar
4. **Edit your profile**: Open [[MY-PROFILE]] and customize anytime

## Keeping COG Updated

COG separates your content from framework files. When new versions are released:
- Run `/update-cog` to check for and apply updates
- Or use the shell script: `./cog-update.sh --check`
- Your braindumps, profiles, and notes are **never** touched by updates

Check your current version: `cat COG-VERSION`

## Tips for Success

- **Don't overthink it**: Just dump your thoughts, COG will help organize
- **Be consistent**: Daily briefs and braindumps work best as habits
- **Review weekly**: Use the weekly-checkin skill to see patterns emerge
- **Evolve your setup**: Edit your profile files anytime or run onboarding again to add projects
- **Stay updated**: Run `/update-cog` periodically to get new skills and improvements

## Getting Help

- Check `SETUP.md` for detailed guides
- Visit the GitHub repo for documentation

**Your second brain is learning about you. Let's begin!**

---

*You can archive or delete this welcome guide once you're comfortable with COG.*
