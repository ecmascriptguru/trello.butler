# Infographic Outreach Board
This is one of Content boards

## Card movements
### Moving cards to list "Planning"
```
when a card is moved into list "Planning", 
for each card linked in the attachments, 
if {labelnames} contains "Campaign", 
remove "content : in progress" label from the card, 
and remove "content : done" label from the card, 
and add "content : todo" label
```

### Moving cards to list "Production", "Fixes Needed" and "Need Approval"
```
when a card is moved into list "Fixes needed" or "Design in progress" or "Needs approval" or "Data+Design", 
for each card linked in the attachments, 
if {labelnames} contains "Campaign", 
remove "content : todo" label from the card, 
and remove "content : done" label from the card, 
and add "content : in progress" label
```

### Moving cards to list "Done"
```
when a card is moved into list "Done", 
for each card linked in the attachments, 
if {labelnames} contains "Campaign", 
remove "content : todo" label from the card, 
and remove "content : in progress" label from the card, 
and add "content : done" label
```

### When a "NEEDS FIX" label added to a card.
```
when "NEEDS FIX" label is added to a card, 
move the card to the bottom of list "Fixes needed", 
and for each card linked in the attachments, 
if "{labelnames}" contains "Campaign", 
and remove "content : todo" label from the card, 
and remove "content : done" label from the card, 
and add "content : in progress" label
``` 



## Archiving synchronization
```
when a card with label is archived, for each card linked in the attachments, archive the card
```

### Checklist synchronization
#### When a checklist added/removed
```
when a checklist is added to a card with label, 
for each card linked in the attachments, 
copy the checklist "{checklistname}" from the trigger card
```

```
when a checklist is removed from a card with label, 
for each card linked in the attachments, 
remove the checklist "{checklistname}" from the card
```

#### When a checklist item added/removed
```
when a checklist item is added to a checklist in a card with label, 
for each card linked in the attachments,
add unique item "{checklistitemname}" to checklist "{checklistname}" on the card
```

```
when a checklist item is removed from a checklist in a card with label, 
for each card linked in the attachments,
remove item "{checklistitemname}" from checklist "{checklistname}"
```

#### When a checklist item was marked as complete/incomplete
```
when a checklist item is checked in a checklist in a card with label, 
for each card linked in the attachments, 
check item "{checklistitemname}" in checklist "{checklistname}"
```

```
when a checklist item is unchecked in a checklist in a card with label, 
for each card linked in the attachments, 
uncheck item "{checklistitemname}" in checklist "{checklistname}"
```

**Please note that there is no feature to synchronize changes in checklist and checklist item names. Once a change was made in a checklist or checklist item, that won't be synchronized no longer.**


## Due Date Synchronization
### Due date add/remove
```
when a due date is added to a card with label, 
for each card linked in the attachments, 
set due on the date in the card
```

```
when a due date is removed from a card with label, 
for each card linked in the attachments, 
remove the due date from the card
```

### Set due date as complete/incomplete
```
when the due date is marked as complete in a card with label, 
for each card linked in the attachments, 
mark the due date as complete
```

```
when the due date is marked as incomplete in a card with label, 
for each card linked in the attachments, 
mark the due date as incomplete
```

## Member synchronizations
### Adding member
```
when someone is added to a card with label, 
for each card linked in the attachments, 
add member @{matchedusername} to the card
```

### Removing member
```
when someone is removed from a card with label, 
for each card linked in the attachments, 
remove member @{matchedusername} from the card
```