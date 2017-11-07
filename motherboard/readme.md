# Trigger and Actions to create a new project

## We will have a list named **Projects**, and a new board should be created with the name of card name automatically whenever an admin create a new card in the **Projects** list of the board named **Motherboard**.

```
when a card is added to list "Projects" by anyone, 
create a new board named "{cardname}" in team "LeanRank", 
and create a new list named "Done" on board "{cardname}" at the top, 
and create a new list named "Ready for Project Review" on board "{cardname}" at the top, 
and create a new list named "Ready for Department Review" on board "{cardname}" at the top, 
and create a new list named "In Progress" on board "{cardname}" at the top, 
and create a new list named "To Do" on board "{cardname}" at the top, 
and create a new list named "Backlog" on board "{cardname}" at the top
```

> This will create a new board with name of the card created by admin, and create lists **Backlog**, **To Do**, **In Progress**, **Ready for Department Review**, **Ready for Project Review** and **Done**

## Or we can easily copy a template board to a new project board. Then we need to have a template board. i.e named with **project_template** and need to copy the board with a name. Let me show you how to do this.
```
when a card is added to list "Projects", 
copy board "template_project" to team "LeanRank" with name "project_{cardname}", 
and add link "{copyboardlink}" in the trigger card
```

```
when a card is added to list "Departments", 
copy board "template_dpt" to team "LeanRank" with name "dpt_{cardname}" ,
and add link "{copyboardlink}" in the trigger card
```