---
layout: page
section: docs
title: Disable or remove SkookumScript in a UE4 project
footer: false
sharing: false

---

### Temporarily disable SkookumScript

1. Locate the following folders:

	- _`MyProject`_`\Scripts`
	- _`MyProject`_`\Content\SkookumScript`<br /><br /> 

2.	Add a minus sign (`-`) at the beginning of these folder names, like so: 
	
	- _`MyProject`_`\-Scripts`
	- _`MyProject`_`\Content\-SkookumScript`<br /><br /> 
	
3. Open `DefaultGame.ini` and comment out the entry that refers to the _`MyProject`_`\Content\SkookumScript` folder. 

SkookumScript is now disabled in your project. To re-enable SkookumScript, simply undo what you did in steps 2 and 3 above.

### Permanently remove SkookumScript

The SkookumScript plugin including commands on the SkookumIDE can still be used, though you won't be able to add custom scripts to your project.

1. Delete these folders:

	- _`MyProject`_`\Scripts`
	- _`MyProject`_`\Content\SkookumScript`<br /><br />
	
2. Open `DefaultGame.ini` and delete the entry that refers to the _`MyProject`_`\Content\SkookumScript` folder.

Your project is now de-Skookified.

If you find yourself deeply regretting your decision to remove SkookumScript, you can always re-Skookify---see [Set up a UE4 project to use SkookumScript](/docs/ue4/setup-sk-proj/).