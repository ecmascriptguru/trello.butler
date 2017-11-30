# Butler actions for department boards


## Adding user trigger
When a user assigned to a card in project board, the user should be assigned to the corresponding card in department board as well. So we can do this as following.
```
when someone is added to a card with label in "Incoming" or "Estimate" or "To Do" or "In Progress" or "Ready for Department Review" or "Ready for Project Review" or "Done" list, 
match "{boardname}" with "dpt__{*}", 
and for each card named "{cardname}" on the board named "project__{labelname}", 
if {labelnames} contains "{wildcard1}", 
add member @{matchedusername} to the card
```

## Removing user trigger
```
when someone is removed from a card with label in "Incoming" or "Estimate" or "To Do" or "In Progress" or "Ready for Department Review" or "Ready for Project Review" or "Done" list, 
match "{boardname}" with "dpt__{*}", 
and for each card named "{cardname}" on the board named "project__{labelname}", 
if {labelnames} contains "{wildcard1}", 
remove member @{matchedusername} from the card
```

## Moving cards
- Moving to list except **Incoming**
```
when a card with label is moved to list "To Do" or "ready for Department Review" or "Ready for Project Review" or "Done", 
match "{boardname}" with "dpt__{*}", 
and for each card named "{cardname}" on board "project__{labelname}", 
if {labelnames} contains "{wildcard1}", 
move the card to list "{listname}" on board "project__{labelname}"
```
- Moving to the **Incoming** list
```
when a card with label is moved to list "Incoming", 
match "{boardname}" with "dpt__{*}", 
and for each card named "{cardname}" on board "project__{labelname}", 
if {labelnames} contains "{wildcard1}", 
move the card to list "Backlog" on board "project__{labelname}"
```

## Adding comment
```
when a comment is posted to a card with label, 
match "{boardname}" with "dpt__{*}", 
and for each card named "{cardname}" on board named "project__{labelname}", 
if {labelnames} contains "{wildcard1}", 
post comment "{commenttext}\n by @{username}"
```

## Due date manipulation
### When a due date is added to or removed from a card
- Adding to a card
```
when a due date is added to a card with label, 
match "{boardname}" with "dpt__{*}", 
and for each card named "{cardname}" on board named "project__{labelname}", 
if {labelnames} contains "{wildcard1}", 
set due on the date in the card
```

- Removing from a card
```
when a due date is removed from a card with label, 
match "{boardname}" with "dpt__{*}", 
for each card named "{cardname}" on board named "project__{labelname}", 
if {labelnames} contains "{wildcard1}", 
remove the due date from the card
```

### When a due date is marked as complete/incomplete in a card
- Marking as **complete**
```
when the due date is marked as complete in a card with label, 
match "{boardname}" with "dpt__{*}", 
for each card named "{cardname}" on board named "project__{labelname}", 
if {labelnames} contains "{wildcard1}", 
mark the due date as complete
```

- Marking as **incomplete**
```
when the due date is marked as incomplete in a card with label, 
match "{boardname}" with "dpt__{*}", 
for each card named "{cardname}" on board named "project__{labelname}", 
if {labelnames} contains "{wildcard1}", 
mark the due date as incomplete
```

## Seting due date when a card moved to In Progress list
```
when a card with label is moved to list "In Progress", 
set due in {{%Estimation}} working days, 
and match "{boardname}" with "dpt__{*}", 
and for each card named "{cardname}" on board "project__{labelname}", 
if {labelnames} contains "{wildcard1}", 
move the card to list "In Progress" on board "project__{labelname}", 
and set due in {{%Estimation}} working days
```


## Managing Checklist
### Adding/Removing Checklist
- Adding a check list
```
when a checklist is added to a card with label, 
match "{boardname}" with "dpt__{*}", 
and for each card on board named "project__{labelname}", 
if {labelnames} contains "{wildcard1}", 
copy the checklist "{checklistname}" from the trigger card
```

- Removing a check list from a card
```
when a checklist is removed from a card with label, 
match "{boardname}" with "dpt__{*}", 
for each card "{cardname}" on board named "project__{labelname}", 
if {labelnames} contains "{wildcard1}", 
remove the "{checklistname}" checklist from the card
```

### Adding/Removing Checklist item
- Adding a checklist item
```
when a checklist item is added to a checklist in a card with label, 
match "{boardname}" with "dpt__{*}", 
and for each card "{cardname}" on board named "project__{labelname}", 
if {labelnames} contains "{wildcard1}", 
add unique item "{checklistitemname}" to checklist "{checklistname}" on the card
```

- Removing a checklist item from a check list
```
when a checklist item is removed from a checklist in a card with label, 
match "{boardname}" with "dpt__{*}", 
for each card "{cardname}" on board named "project__{labelname}", 
if {labelnames} contains "{wildcard1}", 
remove the "{checklistitemname}" item from checklist "{checklistname}"
```

### Checking / Unchecking checklist item
- Checking check list items
```
when a checklist item is checked in a checklist in a card with label, 
match "{boardname}" with "dpt__{*}", 
and for each card "{cardname}" on board named "project__{labelname}", 
if {labelnames} contains "{wildcard1}", 
check item "{checklistitemname}" in checklist "{checklistname}"
```

- Unchecking check list items
```
when a checklist item is unchecked in a checklist in a card with label, 
match "{boardname}" with "dpt__{*}", 
and for each card "{cardname}" on board named "project__{labelname}", 
if {labelnames} contains "{wildcard1}", 
uncheck item "{checklistitemname}" in checklist "{checklistname}"
```