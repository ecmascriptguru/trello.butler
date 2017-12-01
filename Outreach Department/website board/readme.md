# Website layer board.

## Lists on this board
### Backlog
> There are different types of work here. Notice the infographic label, it doesn't go to the content board until moved into "Todo". The work types are "wordpress", "issue" and "infographic".

### Todo
> In this stage the infographic goes to the content board and waits in the incoming list. When it is started in the content department it moves to in progress on this website board.

### Doing
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

> `outreach: done`


## Butler commands by specification
### Card duplication
#### When a card with _infographic_ label moved to `Todo` list, the card should be duplicated in `Incoming` list on **Outreach** board and **Infographic Production** board. 

We suppose that website board was already named with a specific pattern like __Website Demo Board: `Betfy`__. Here `Betfy` is website name and it should be added as a label on outreach board, and `Website: Betfy` label will be added to the duplicated card on **Infographic Production** Board. That's how a card will have 2 card links connected each other.
```
when a card with "infographic" label is moved into list "Todo", 
match "{boardname}" with "Website Demo Board: {*}", 
and create a card with title "{cardname}" in list "Incoming" on the board named "Outreach Board", 
and copy all the members, and all the attachments and the description and all the checklists and the due date from the trigger card, 
and add "{wildcard1}" label to the card, 
and link the cards together in the attachments, 
and create a card with title "{cardname}" in list "Incoming" on the board named "Infographic Production Board", 
and copy all the members and all the attachments and the description and all the checklists and the due date from the trigger card, 
and add "Website: {wildcard1}" label to the card,
and link the cards together in the attachments,
and for each card named "{cardname}" in list "Incoming" on the board named "Outreach Board", 
if {labelnames} contains "{wildcard1}", 
add link "{newcardlink}" join the card
```

### Checklist synchronization
### When a checklist added/removed
```
when a checklist is added to a card with "infographic" label, 
and for each card linked in the attachments, 
copy the checklist "{checklistname}" from the trigger card
```

```
when a checklist is removed from a card with "infographic" label, 
for each card linked in the attachments, 
remove the checklist "{checklistname}" from the card
```

### When a checklist item added/removed
```
when a checklist item is added to a checklist in a card with "infographic" label, 
for each card linked in the attachments,
add unique item "{checklistitemname}" to checklist "{checklistname}" on the card
```

```
when a checklist item is removed from a checklist in a card with "infographic" label, 
for each card linked in the attachments,
remove item "{checklistitemname}" from checklist "{checklistname}" on the card
```

### When a checklist item was marked as complete/incomplete
```
when a checklist item is checked in a checklist in a card with label "infographic", 
for each card linked in the attachments, 
check item "{checklistitemname}" in checklist "{checklistname}"
```