# Outreach Department Board
We will see butler commands on how to synchronize cards across corresponding boards

## Lists
Here we will have the following lists
### Incoming
    This list will have the out piece that was assigned from another department or website. The label indicates which website it comes from.
### Legend

### Infographic Outreach

### Content Outreach

### Outreach in Progress
    A calculation is done based on the number of targets as to when the finish date should be. This date is auto added to the card. Also the custom field remaining targets is added in this stage - it pulls directly from the mailshake api and updates each card once per day.

### Completed Campaign

## Card duplication
### In case of Infographic Outreach
```
when a card with label is moved into list "Infographic Outreach", 
create a card with title "{cardname}" in list "Incoming" on "Infographic Production" board, 
and copy all the members and the description and all the checklists and due date and all the attachments from the trigger card, 
and add "Website: {labelname}" label, 
and link the cards together in the attachments, 
and for each card named "{cardname}" on the board named "Website: {labelname}", 
if {labelnames} contains "campaign", 
add link "{newcardlink}", 
and find a card named "{cardname}" on the board named "Website: {labelname}", 
and remove "outreach : todo" from the card, 
and remove "outreach : done" label from the card, 
and add "outreach : in progress" label
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

## Card Movements
### Moving to **Todo** list
```
when a card with label is moved into "Todo" list, 
find a card named "{cardname}" on the board named "Website: {labelname}", 
and remove "outreach : in progress" label from the card, 
and remove "outreach : done" label from the card, 
and add "outreach : todo" label
```

### Moving to **Content Outreach** list
```
Not specified yet
```

### Moving to **Outreach in Progress** list
```
when a card with label is moved into "Outreach in Progress" list, 
find a card named "{cardname}" on the board named "Website: {labelname}", 
and remove "outreach : todo" label from the card, 
and remove "outreach : done" label from the card, 
and add "outreach : in progress" label
```

### Moving to **Completed Campaign**
```
when a card with label is moved into "Completed Campaign" list,
find a card named "{cardname}" on the board named "Website: {labelname}",
and remove "outreach : todo" label from the card,
and remove "outreach : in progress" label from the card,
and add "outreach : done" label,
and move the card into list "Done"
```