# Action trigger for a new task/card of ***Backlog** list of a project board.

When a project manager create a new card in **Backlog** list of a project board, set something like card description, due date, attachment, members and add a label(department), this card should be copied to the corresponding department boards including description, due date, check list, members, etc.
In contrary, removing label should work in the department board as well.

## Adding a label/department to a card

``` 
when a label is added to a card in list "Backlog", 
match "{boardname}" with "project__{*}", 
and create a card with title "{cardname}" in list "Incoming" on the board named "dpt__{labelname}", 
and add link "{triggercardlink}", 
and copy all the members and the description and all the checklists and the due date from the trigger card, 
and add "{wildcard1}" label to the card
```

> Intereted a bit.
```
when a label is added to a card in list "Backlog", copy the card to list "Incoming" on board "{labelname}" and add link "{triggercardlink}" to the card
```

## Removing a label/department from a card
```
when a label is removed from a card in "Backlog" list, 
match "{boardname}" with "project__{*}", 
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