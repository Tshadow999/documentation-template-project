
## Last updated

| Version | Date       | Author | Commit |
| ------- | ---------- | ------ | ------ |
| v1.0.0  | 2026-04-13 | Tycho  |        |

---

## Purpose
Be able to setup the development environment to be able to make changes on the project.

## Content

1. Have obsidian installed
2. Enable community plugins
3. Add Excalidraw plugin by Zsolt Viczian
4. Add Diagrams plugin by Sam Greenhalgh
5. Read the [[Introduction]] and [[Project Summary]] again
6. Read [[Obsidian Templates]] before making a new feature

### Guide to use DrawIO plugin

To edit an existing svg either:
- Right click the name and look for edit diagram.
- Open the svg and look for a pencil icon in the top right of obsidian

To make a new drawing (svg) either:
- Use `Control + P` to enter a command and type: "diagram"
	- Then press enter once the `Diagrams: Create a new diagram` is selected.
- Right click on a directory and look for the `New Diagram` option

To embed the drawing use the linking syntax but prepend an exclamation mark (!):
- Like so: `![[ModbusDiagramClasses.svg]]`

### Guide to use Excalidraw plugin

To edit an existing drawing simply:
- Click on the name to open the drawing

To make a new drawing either:
- Use `Control + P` to enter a command and type: "excalidraw create"
	- Then press enter once any of the  `Excalidraw: Create new drawing - X` is selected.
- Right click on a directory and look for the `New Drawing` option.

To embed the drawing use either:
- Use `Control + P` to enter a command and type: "excalidraw embed"
	- Then press enter once  `Excalidraw: Embed a drawing` is selected.
		- Then choose your drawing
	- You can also use `Excalidraw: Embed the most recent edited drawing`.
- Use the linking syntax like with the drawIO plugin.
	- Like so: `![[ModbusDiagramArchitecture]]`
