# Butler actions for department boards


## Adding user trigger
When a user assigned to a card in project board, the user should be assigned to the corresponding card in department board as well. So we can do this as following.
```
when someone is added to a card with label in "Incoming" list or "Estimate" list or "To Do" list or "In Progress" list or "Ready for Department Review" list or "Ready for Project Review" list or "Done" list, 
find a card named "{cardname}" on the board named "{labelname}",
and add member @{matchedusername} to the card
```

## Removing user trigger
```
when someone is removed from a card with label in "Incoming" list or "Estimate" list or "To Do" list or "In Progress" list or "Ready for Department Review" list or "Ready for Project Review" list or "Done" list, 
find a card named "{cardname}" on the board named "{labelname}",
and remove member @{matchedusername} from the card
```

## Adding comment
```
when a comment is posted to a card with label, find a card named "{cardname}" on board named "{labelname}", and post comment "{commenttext}\n by @{username}"
```