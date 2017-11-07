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
when a card with label is moved to list "To Do" or "In Progress" or "ready for Department Review" or "Ready for Project Review" or "Done", 
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