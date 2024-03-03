In general as you edit diagrams in the wiki, the GitHub web UI experience
works better as you can toggle between editing and previews:

![image](https://github.com/binkley/wiki-docs/assets/186421/8b41ba18-338a-4311-9ec7-8668cd8a1003)

You key goto resource on Mermaid is [_About
Mermaid_](https://mermaid.js.org/intro/) (the documentation for each diagram
type).
* Typically in architecture you use the "Flowchart" type which shows
  relationships among parts of your system;
  this is the kind of diagram you might draw at a whiteboard
* "Sequence Diagram" is helpful to clarify the order of interactions
* "Entity Relationship Diagram" is great for documenting your database, and
  works to describe structure and properties in your JSON
* For developers working in the code base, "Class Diagram" is a classic but
  not typically shown outside your team

## Simple example

Here is a simple diagram with Mermaid.
You can embed this directly in your wiki documentation using a code fence.<br/>
You may find that reordering nodes and connections gives a better overall
diagram.

```mermaid
---
Title: Simple example
---
flowchart LR
  UI[Your UI]
  API[Your API]

UI -->|This is UI calling API| API
API -->|This is API responding| UI
```
