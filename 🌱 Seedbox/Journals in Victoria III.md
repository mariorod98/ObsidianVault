up:: [[⚔️ Cluasewitz Engine]]
tags:: #state/seedling #on/clausewitz/victoriaIII

# Journals in Victoria III
A journal entry is a sort of mission/quest system in Victoria III.

For journals to be made available to a certain country, game logic needs to add them to the country using this effect.

```
add_journal_entry = {type = your_journal_entry_name}
```

You can add a new journal entry in a few different ways:
1. To create a starter journal, you need to add it to the country history file.
2. Inside the immediate trigger which is used in Decisions, Events and Journals.
3. Inside the *on_complete* trigger which is used in...
---
Planted: 2022-12-16
Last tended: 2022-12-16