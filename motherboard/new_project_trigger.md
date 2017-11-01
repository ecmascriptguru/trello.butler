# Trigger and Actions to create a new project

We will have a list named **Projects**, and a new board should be created with the name of card name automatically whenever an admin create a new card in the **Projects** list of the board named **Motherboard**.

```
when a card is added to list "Projects" by anyone, 
create a new board named "{cardname}" in team "Jing Dong", 
and create a new list named "Done" on board "{cardname}" at the top, 
and create a new list named "Ready for Project Review" on board "{cardname}" at the top, 
and create a new list named "Ready for Department Review" on board "{cardname}" at the top, 
and create a new list named "In Progress" on board "{cardname}" at the top, 
and create a new list named "To Do" on board "{cardname}" at the top, 
and create a new list named "Backlog" on board "{cardname}" at the top
```

> This will create a new board with name of the card created by admin, and create lists **Backlog**, **To Do**, **In Progress**, **Ready for Department Review**, **Ready for Project Review** and **Done**