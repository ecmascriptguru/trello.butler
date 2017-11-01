# Action trigger for a new task/card of ***Backlog** list of a project board.

When a project manager create a new card in **Backlog** list of a project board, set something like card description, due date, attachment, members and add a label(department), this card should be copied to the corresponding department boards including description, due date, check list, members, etc.
In contrary, removing label should work in the department board as well.

## Adding a label/department to a card
```
when a label is added to a card in list "Backlog" by anyone, 
find or create a card with title "{cardname}" and description "{carddescription}" in list "Incoming" on the board named "{labelname}", 
and copy all the members and the description and all the checklists and the due date from the trigger card,
and add "{boardname}" label to the card
```

## Removing a label/department from a card
```
when a label is removed from a card in list "Backlog" by anyone, 
find a card with title "{cardname}" in list "Incoming" on the board named "{labelname}",
and archive the card
```