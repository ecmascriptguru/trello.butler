# Website layer board.

## Lists on this board
### Legend
> To give

### Backlog
> There are different types of work here. Notice the campaign label, it doesn't go to the content board until moved into "Sprint Planning". The work types are "wordpress", "issue" and "campaign".

### Sprint Planning
> In this stage the campaign goes to the content board and waits in the incoming list. When it is started in the content department it moves to in progress on this website board.

### Current Sprint

### In Progress
> In this list, we will have all cards that are in progress in other boards like content board and outreach board. In order to show the status we will use labels. So the label names will be like "{board_name} : {status}". So this feature will be implemented in other boards like department board(outreach board) and sub process board.

### Done
> When a content and outreach is done it is moved to the done category.

## Labels
### Status on outreach board
> `outreach: todo`

> `outreach: in progress`

> `outreach: done`

### Status on content board
> `content: todo`

> `content: in progress`

> `content: done`


## Butler commands by specification
### Card duplication
#### When a card with _campaign_ label moved to `Sprint Planning` list, the card should be duplicated in `Incoming` list on **Outreach** board and **Infographic Production** board. 

We suppose that website board was already named with a specific pattern like __Website: `Betfy`__. Here `Betfy` is website name and it should be added as a label on outreach board, and `Website: Betfy` label will be added to the duplicated card on **Infographic Production** Board. That's how a card will have 2 card links connected each other.
```
when a card with "campaign" label is moved into list "Sprint Planning", 
match "{boardname}" with "Website: {*}", 
and create a card with title "{cardname}" in list "Incoming" on the board named "Outreach", 
and copy all the members, and all the attachments and the description and all the checklists and the due date from the trigger card, 
and add "{wildcard1}" label to the card, 
and link the cards together in the attachments, 
and create a card with title "{cardname}" in list "Incoming" on the board named "Infographic Production", 
and copy all the members and all the attachments and the description and all the checklists and the due date from the trigger card, 
and add "Website: {wildcard1}" label to the card,
and link the cards together in the attachments,
and for each card named "{cardname}" in list "Incoming" on the board named "Outreach", 
if {labelnames} contains "{wildcard1}", 
add link "{newcardlink}" join the card
```

In this case, we just duplicate the moved card on the outreach board, because it should be duplicated on differetn boards according to content. Especially it can be duplicated on Infographic Outreach board or Content Outreach board. So it will be managed on outreach board
```
when a card with "campaign" label is moved into list "Sprint Planning",
match "{boardname}" with "Website: {*}",
and create a card with title "{cardname}" in list "Incoming" on the board "Outreach",
and copy all the members and all the attachments and the description and all the checklists and all the members and the due date from the trigger card,
and add "{wildcard1}" label to the card,
and link the cards together in the attachments
```

## When a card is archived
```
when a card with "campaign" label is archived,
for each card linked in the attachments,
archive the card
```

### Checklist synchronization
#### When a checklist added/removed
```
when a checklist is added to a card with "campaign" label, 
for each card linked in the attachments, 
copy the checklist "{checklistname}" from the trigger card
```

```
when a checklist is removed from a card with "campaign" label, 
for each card linked in the attachments, 
remove the checklist "{checklistname}" from the card
```

#### When a checklist item added/removed
```
when a checklist item is added to a checklist in a card with "campaign" label, 
for each card linked in the attachments,
add unique item "{checklistitemname}" to checklist "{checklistname}" on the card
```

```
when a checklist item is removed from a checklist in a card with "campaign" label, 
for each card linked in the attachments,
remove item "{checklistitemname}" from checklist "{checklistname}"
```

#### When a checklist item was marked as complete/incomplete
```
when a checklist item is checked in a checklist in a card with label "campaign", 
for each card linked in the attachments, 
check item "{checklistitemname}" in checklist "{checklistname}"
```

```
when a checklist item is unchecked in a checklist in a card with label "campaign", 
for each card linked in the attachments, 
uncheck item "{checklistitemname}" in checklist "{checklistname}"
```

**Please note that there is no feature to synchronize changes in checklist and checklist item names. Once a change was made in a checklist or checklist item, that won't be synchronized no longer.**


## Due Date Synchronization
### Due date add/remove
```
when a due date is added to a card with "campaign" label, 
for each card linked in the attachments, 
set due on the date in the card
```

```
when a due date is removed from a card with "campaign" label, 
for each card linked in the attachments, 
remove the due date from the card
```

### Set due date as complete/incomplete
```
when the due date is marked as complete in a card with "campaign" label, 
for each card linked in the attachments, 
mark the due date as complete
```

```
when the due date is marked as incomplete in a card with "campaign" label, 
for each card linked in the attachments, 
mark the due date as incomplete
```

## Comments Synchronization
Every comment posted on this website board should be duplicated in other corresponding boards like **Outreach** board and **Infographic Production**

```
when a comment is posted to a card with "campaign" label, 
for each card linked in the attachments, 
post comment "{commenttext}\n by @{username}"
```

## Member synchronizations
### Adding member
```
when someone is added to a card with "campaign" label, 
for each card linked in the attachments, 
add member @{matchedusername} to the card
```

### Removing member
```
when someone is removed from a card with "campaign" label, 
for each card linked in the attachments, 
remove member @{matchedusername} from the card
```
