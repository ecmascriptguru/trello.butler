# Action trigger for a new task/card of **Backlog** list of a project board.

When a project manager create a new card in **Backlog** list of a project board, set something like card description, due date, attachment, members and add a label(department), this card should be copied to the corresponding department boards including description, due date, check list, members, etc.
In contrary, removing label should work in the department board as well.

## Adding a label/department to a card

``` 
when a label is added to a card in list "Backlog", 
match "{boardname}" with "project__{*}", 
and create a card with title "{cardname}" in list "Incoming" on the board named "dpt__{labelname}", 
and copy all the members and the description and all the checklists and the due date from the trigger card, 
and add "{wildcard1}" label to the card, 
and link the cards together in the attachments
```

> Intereted a bit.
```
when a label is added to a card in list "Backlog", copy the card to list "Incoming" on board "{labelname}" and add link "{triggercardlink}" to the card
```

## Removing a label/department from a card
```
when a label is removed from a card in "Backlog" list, 
remove attachment "{*}", 
and match "{boardname}" with "project__{*}", 
and for each card named "{cardname}" in list "Incoming" on the board named "dpt__{labelname}", 
and if {labelnames} contains "{wildcard1}", 
archive the card
```

> Intereted a bit.
```
when a label is removed from a card in list "Backlog",
find the card "{cardname}" in list "Incoming" on board "{labelname}" and archive the card
```


## Adding user trigger
When a user assigned to a card in project board, the user should be assigned to the corresponding card in department board as well. So we can do this as following.
```
when someone is added to a card with label in "Backlog" or "To Do" or "In Progress" or "Ready for Department Review" or "Ready for Project Review" or "Done" list, 
match "{boardname}" with "project__{*}", 
and for each card named "{cardname}" on the board named "dpt__{labelname}", 
if {labelnames} contains "{wildcard1}", 
add member @{matchedusername} to the card
```

## Removing user trigger
```
when someone is removed from a card with label in "Backlog" or "To Do" or "In Progress" or "Ready for Department Review" or "Ready for Project Review" or "Done" list, 
match "{boardname}" with "project__{*}", 
and for each card named "{cardname}" on the board named "dpt__{labelname}", 
if {labelnames} contains "{wildcard1}", 
remove member @{matchedusername} from the card
```

## Moving a card to a list on project board, the corresponding card should be moved on department board as well.
```
when a card with label is moved into list "To Do" or "In Progress" or "Ready for Department Review" or "Ready for Project Review" or "Done", 
match "{boardname}" with "project__{*}", 
and for each card named "{cardname}" on board "dpt__{labelname}", 
if {labelnames} contains "{wildcard1}", 
move the card to list "{listname}" on board "dpt__{labelname}"
```
> When a card moved to **Backlog** list, then the corresponding card should be moved to **incoming** list again.
```
when a card with label is moved into list "Backlog", 
match "{boardname}" with "project__{*}", 
and for each card named "{cardname}" on board "dpt__{labelname}", 
if {labelnames} contains "{wildcard1}", 
move the card to list "Incoming" on board "dpt__{labelname}"
```

## Action for comments in project board.
```
when a comment is posted to a card with label, 
match "{boardname}" with "project__{*}", 
and for each card named "{cardname}" on board named "dpt__{labelname}", 
if {labelnames} contains "{wildcard1}", 
post comment "{commenttext}\n by @{username}"
```

```
when a comment is posted to a card, find the card linked in the description and post comment "{commenttext} by @username"
```

## Due date manipulating
### When a due date is added to or removed from a card
- Adding a due date
```
when a due date is added to a card with label, 
match "{boardname}" with "project__{*}", 
and for each card named "{cardname}" on board named "dpt__{labelname}", 
if {labelnames} contains "{wildcard1}", 
set due on the date in the card
```

- Removing a due date
```
when a due date is removed from a card with label, 
match "{boardname}" with "project__{*}", 
for each card named "{cardname}" on board named "dpt__{labelname}", 
if {labelnames} contains "{wildcard1}", 
remove the due date from the card
```

### When a due date is marked as complete/incomplete in a card.
- Marking as complete
```
when the due date is marked as complete in a card with label, 
match "{boardname}" with "project__{*}", 
for each card named "{cardname}" on board named "dpt__{labelname}", 
if {labelnames} contains "{wildcard1}", 
mark the due date as complete
```

- Marking as incomplete
```
when the due date is marked as incomplete in a card with label, 
match "{boardname}" with "project__{*}", 
for each card named "{cardname}" on board named "dpt__{labelname}", 
if {labelnames} contains "{wildcard1}", 
mark the due date as incomplete
```

## Managing Checklist
### Adding/Removing Checklist
- Adding a check list
```
when a checklist is added to a card with label, 
match "{boardname}" with "project__{*}", 
and for each card on board named "dpt__{labelname}", 
if {labelnames} contains "{wildcard1}", 
copy the checklist "{checklistname}" from the trigger card
```

- Removing a check list from a card
```
when a checklist is removed from a card with label, 
match "{boardname}" with "project__{*}", 
for each card "{cardname}" on board named "dpt__{labelname}", 
if {labelnames} contains "{wildcard1}", 
remove the "{checklistname}" checklist from the card
```

### Adding/Removing Checklist item
- Adding a checklist item
```
when a checklist item is added to a checklist in a card with label, 
match "{boardname}" with "project__{*}", 
and for each card "{cardname}" on board named "dpt__{labelname}", 
if {labelnames} contains "{wildcard1}", 
add unique item "{checklistitemname}" to checklist "{checklistname}" on the card
```

- Removing a checklist item from a check list
```
when a checklist item is removed from a checklist in a card with label, 
match "{boardname}" with "project__{*}", 
for each card "{cardname}" on board named "dpt__{labelname}", 
if {labelnames} contains "{wildcard1}", 
remove the "{checklistitemname}" item from checklist "{checklistname}"
```

### Checking / Unchecking checklist item
- Checking check list items
```
when a checklist item is checked in a checklist in a card with label, 
match "{boardname}" with "project__{*}", 
and for each card "{cardname}" on board named "dpt__{labelname}", 
if {labelnames} contains "{wildcard1}", 
check item "{checklistitemname}" in checklist "{checklistname}"
```

- Unchecking check list items
```
when a checklist item is unchecked in a checklist in a card with label, 
match "{boardname}" with "project__{*}", 
and for each card "{cardname}" on board named "dpt__{labelname}", 
if {labelnames} contains "{wildcard1}", 
uncheck item "{checklistitemname}" in checklist "{checklistname}"
```