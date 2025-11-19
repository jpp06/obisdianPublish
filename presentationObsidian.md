
<style>
	.blue-back {
		color: red;
		 background-color: blue;
	}
	.with-border {
		border: 1px solid red;
	}
</style>


#### Un caillou dans une galaxie 
![[galaxyLogo.png]]

---

<grid drag="90 30" drop="top">
# introduction

[landing](https://obsidian.md)
et c'est le <span class="blue-back">drame !</span>

</grid>

<grid drag="50 55" drop="5 30">
<split even gap="0" no-margin wrap="3" align="justify">
![[spark.png|400]]
![[publish.png|400]]
![[sync.png|400]]
</split>
</grid>

<grid drag="45 55" drop="-5 30">
![[galaxy.png|400]]
</grid>

<grid drag="90 15" drop="bottom">
![[markdownWhat.png|200]]
</grid>

note: pour moi

---

![[markdown.png]]

# <span class="blue-back">++ </span> 

basiquement pas wysiwyg

# MAIS 

---

# plugins

14 novembre 2025 : 2676 !


---
# MD editor

- hybrid MD mode : deux modes d'édition (le livre) selon "source mode" ou non
	- source mode : sous `...`, toggle plus ou moins de détails
- reading view : le crayon
	- affichage lisible

![[sourceReading.png]]
- vertical split: split right et ensuite "crayon" (command-click sur le livre)
---

# Bien commencer

avec un fil rouge<!-- element style="color:red" -->

- feuille de temps et activités
- présentations
- dessins
- charts

trouver les bons plugins <!-- element style="background:blue" -->

---
# Feuille de temps et activités

- [tasks](https://github.com/obsidian-tasks-group/obsidian-tasks) : base pour les activités
- ![[tasks_plugin_acme.png|400]]

- [dataview](https://github.com/blacksmithgu/obsidian-dataview) : vault as a database via API, JavaScript

- [journal](https://github.com/srg-kostyrko/obsidian-journal) : organiser ses notes

---
# tasks (plugin)

![[tasks.png]]
---
# tasks (plugin)

- commencer petit

````markdown
   ```tasks

   ```
````

![[tasks_plugin_mini.png]]

---
# tasks (plugin)
- filtrage
 
````markdown
```tasks
(tags includes AM) OR (tags includes PM)
short mode
hide edit button
hide backlink
```
````

![[tasks_plugin_filter.png]]


---
# dataview (plugin)


````markdown
```dataview
TASK
WHERE contains(tags, "#AM") OR contains(tags, "#PM")
GROUP BY file.link
```
````

---
# dataviewjs (plugin)

````markdown
```dataviewjs

function minutes(str) {
  let items = str.split(" ");
  let startItems = items[0].split(":"),
      endItems = items[1].split(":");
  let result = +endItems[0] * 60 + +endItems[1] - (+startItems[0] * 60 + +startItems[1])
  return result
};
function hm(minutes) {
  return String(Math.floor(minutes / 60)).padStart(2, "0") + ":" + String(minutes % 60).padStart(2, "0")
};

let tasks = dv.pages()
  .where(p => p.file && p.file.path && !p.file.path.includes("templates/"))
  .file.tasks.filter(t => ['#AM', '#PM'].some(tag => t.tags.includes(tag)));

let tableData = [];
for (let group of tasks.groupBy(t => t.path)) {
  let pathItems = group.key.split("/")
  let date = pathItems[pathItems.length - 1].split(".")[0]
  let dailies = group.rows
  let am = dailies[0]
  let pm = dailies[1]
  let totalMinutes = minutes(am.text) + minutes(pm.text)
  let duration = hm(totalMinutes)
  let details = am.text + " " + pm.text
  tableData.push([date, duration, details])
}

dv.table(["Date", "Durée", "Détails"], tableData)
```
````


---
# journal (plugin)

````markdown

````


---

# Général

- [advanced slides](https://github.com/MSzturc/obsidian-advanced-slides)
- [git](https://github.com/Vinzent03/obsidian-git) just do git!
- [excalidraw](https://github.com/zsviczian/obsidian-excalidraw-plugin)

---

## WoW AH

- [charts](https://github.com/phibr0/obsidian-charts)