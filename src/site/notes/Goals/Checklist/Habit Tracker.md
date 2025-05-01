---
{"dg-publish":true,"permalink":"/goals/checklist/habit-tracker/","created":"Apr 22, 2024, 11:48 AM"}
---



To track habits, see [[Goals/Checklist/Habits/Habit Database\|Habit Database]]. For documentation, visit [obsidian-tracker](https://github.com/pyrochlore/obsidian-tracker/blob/master/examples/TestDateFormats.md#relative-date-input-for-startdate-and-enddate).

```tracker
searchType: frontmatter
searchTarget: Bible, Pray, Scripture_Typer,Sing_Hymns, Make_Bed, iRestore_Treatment, Flexbelt, Gym, Run, Clean_Room, Duolingo, NoFap, Tiege_Hanley, Pushups
folder: Goals/Checklist/Habits
datasetName: Bible, Pray, Scripture Typer, Sing Hymns, Make Bed, iRestore Treatment, Flexbelt, Gym, Run, Clean Room, Duolingo, NoFap, Tiege Hanley, Pushups
month:
	startWeekOn: 'Mon'
```
```tracker
searchType: frontmatter
searchTarget: Bible, Pray
folder: Goals/Checklist/Habits
datasetName: Bible, Pray
endDate: 0d
summary:
	template: "AVERAGES\nBible: {{average(dataset(0))}} minutes\nPray: {{average(dataset(1))}}"
```

```tracker
searchType: frontmatter
searchTarget: Bible, Pray
folder: Goals/Checklist/Habits
datasetName: Bible, Pray
endDate: 0d

line:
	title: Habits
	lineColor: green, blue
	showLegend: true
	legendOrientation: vertical
	fillGap: true
```

```tracker
searchType: frontmatter
searchTarget: Pushups
folder: Goals/Checklist/Habits
endDate: 0d

line:
	title: Pushups
	fillGap: true
```

```tracker
searchType: frontmatter
searchTarget: Bench_Press, Barbell_Bench_Press, Lat_Pulldown, Overhead_Press, Cable_Fly
folder: Goals/Checklist/Habits
datasetName: Bench Press, Barbell Bench Press, Lat Pulldown, Overhead Press, Cable Fly
endDate: 0d

line:
	title: Habits
	lineColor: green, blue, red, yellow, orange
	showLegend: true
	yAxisLabel: lb
	legendOrientation: vertical
	fillGap: true
```
