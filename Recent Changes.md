**This displays the most recent changes made to the Player-Vault. If the table is broken, please contact your DM.**

-------------------------------------------------------------------------
```dataview
table dateformat(file.mtime, "MMMM dd, HH:mm") as "Last Modified"
from "player-vault"
where file.name != "Author"
sort file.mtime desc
limit 5
```
