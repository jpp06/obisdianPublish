---
width: 1000
height: 800
---


<style>
	.blue-back {
		color: red;
		 background-color: blue;
	}
	.with-border {
		border: 1px solid red;
	}
	.md-typeset pre > code {
	    max-height: 15rem;
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

# ET... 

---

# plugins

14 novembre 2025 : <span style="color:red;">2676</span> !

A vot' bon coeur, y en a pour tous les goûts !


---
<grid drag="90 10" drop="5 0">
# MD editor
</grid>

<grid drag="90 85" drop="5 13" align="left">
- hybrid MD mode : deux modes d'édition (le livre) selon "source mode" ou non
	- source mode : sous `...`, toggle plus ou moins de détails

![[sourceMode.png|200]]<!-- element align="center" -->

- reading view : le crayon. affichage lisible 


![[sourceReading.png|600]]<!-- element align="center" -->

- preview : split right et ensuite "crayon" (command-click sur le livre)
</grid>
---

# Et mes données ?

- du texte (markdown, js, autres)
	- lisible
	- automatisations
- sur ta machine !
	- sauvegardes
	- git
- modèle commercial
	- vend la synchro multi-devices (4$/mois)
	- vend l'exposition internet (8$/mois)

---
<grid drag="95 10" drop="5 0">
# Bien commencer ?
</grid>

<grid drag="90 15" drop="5 18" align="center">
avec un fil rouge<!-- element style="color:red;" -->
</grid>

<grid drag="90 70" drop="5 22" align="left">
- feuille de temps et activités
- présentations
- dessins
- charts
</grid>

<grid drag="90 15" drop="5 85">
trouver les bons plugins <!-- element style="background:blue" -->
</grid>

---

# Feuille de temps et activités

![[horariresActivites.png]]

---
# Feuille de temps et activités

- [tasks](https://github.com/obsidian-tasks-group/obsidian-tasks) : base pour les activités
- ![[tasks_plugin_acme.png|400]]

- [dataview](https://github.com/blacksmithgu/obsidian-dataview) : vault as a database via API, JavaScript

- [journal](https://github.com/srg-kostyrko/obsidian-journal) : organiser ses notes

---
<grid drag="95 10" drop="5 0">
# tasks (plugin)
</grid>

<grid drag="45 90" drop="5 15" align="left">
![[tasks.png|350]]
</grid>

<grid drag="45 90" drop="55 15" align="left">
![[taskDaily.png|350]]
</grid>

---
<grid drag="95 10" drop="5 0">
# tasks (plugin)
</grid>

<grid drag="95 10" drop="5 15" align="left">
- commencer petit
</grid>

<grid drag="95 70" drop="5 28">
````markdown
   ```tasks

   ```
````

![[tasks_plugin_mini.png|500]]
</grid>

---
<grid drag="95 10" drop="5 0">
# tasks (plugin)
</grid>

<grid drag="95 10" drop="5 15" align="left">
- filtrage
 </grid>

<grid drag="70 80" drop="0 28">
````markdown
```tasks
(tags includes AM) OR (tags includes PM)
short mode
hide edit button
hide backlink
```
````
</grid>
<grid drag="30 80" drop="70 28">
![[tasks_plugin_filter.png|300]]
</grid>

---
<grid drag="95 10" drop="5 0">
# dataview (plugin)
</grid>

<grid drag="95 10" drop="5 15" align="left">
- on prépare la suite
</grid>

<grid drag="95 80" drop="5 28">

````markdown
```dataview
TASK
WHERE contains(tags, "#AM") OR contains(tags, "#PM")
GROUP BY file.link
```
````

![[dataview.png|500]]
</grid>

---

<grid drag="95 10" drop="5 0">
# dataviewJs
</grid>

<grid drag="95 10" drop="5 15" align="left">
- Enfin !
</grid>

<grid drag="100 90" drop="0 25" style="font-size: 20px;" align="center">

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
</grid>

---

# dataviewJs

![[dataviewJs.png]]

---

<grid drag="95 10" drop="5 0">
# journal (plugin)
</grid>

<grid drag="35 80" drop="5 10" style="font-size: 32px;">
````markdown

# calendar
```calendar-timeline
mode: month
```

# shelf Work
```journals-home
show:
  - day
scale: 2
separator: " | "
shelf: Work
```
````
</grid>

<grid drag="55 80" drop="40 10">
![[journal.png|500]]
</grid>

---

# Présentations

C'est pas powerpoint ou prezi

![[advSlidesExample.png]]
---

# Advanced slides

- pas wysiwyg
	- layouts
	- css
- export HTML (dans preview)
	- github pages
- efforts sur un template ?

- [advanced slides](https://github.com/MSzturc/obsidian-advanced-slides)


---

# Annoter des copies d'écran

- re-tester IA
- et sans doute beaucoup d'autres choses

---

# excalidraw


![[issuesGithub.png]]

- [excalidraw](https://github.com/zsviczian/obsidian-excalidraw-plugin)


---

# des séries

![[series.png]]

---

# charts (plugin)

- pas très riche en type de charts
- rapide et unifié
- éditable et écrivable
	- mode texte comme le reste
- [charts](https://github.com/phibr0/obsidian-charts)

---

# git (plugin)

- ToDo

- [just do git!](https://github.com/Vinzent03/obsidian-git)
---
