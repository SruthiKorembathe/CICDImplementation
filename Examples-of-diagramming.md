_Everyone loves diagrams!_

Be liberal in the use of diagrams in your wiki.
These rely on use of `Mermaid.js` syntax embedded in your pages.
It is a solid feature of GitHub, and you should take advantage of what your
tools provide.

> [!TIP]
> In general as you edit diagrams in the wiki, unless you are comfortable with
> direct syntax editing and visualizing the results, the GitHub web UI
> experience is better as you toggle between "Write" (edit) and "Preview"
> modes:

![Editing Examples of diagramming](example-diagramming.png "Editing Examples of diagramming")

## OK, but where I can learn more about diagramming in my wiki?

Your key goto resource on Mermaid is [_About
Mermaid_](https://mermaid.js.org/intro/) (the documentation for each diagram
type).
* Typically, in architecture you use the
  [_Flowchart_](https://mermaid.js.org/syntax/flowchart.html) type to show
  relationships among parts of your system; this is the kind of diagram you
  might draw on a whiteboard.
* [_Sequence Diagram_](https://mermaid.js.org/syntax/sequenceDiagram.html) is
  helpful to clarify the order of interactions. A typical example is a UI
  "lane" on the left, your API in the middle, and a DB on the right.
* [_Entity Relationship
  Diagram_](https://mermaid.js.org/syntax/entityRelationshipDiagram.html) is
  great for documenting your database and also your JSON structure and
  properties.
* For developers working in the code base, [_Class
  Diagram_](https://mermaid.js.org/syntax/classDiagram.html) is a classic but
  not typically shown outside your team.

## Simple flowchart example

Here is a simple diagram (flowchart) with Mermaid.
You can embed this directly in your wiki documentation using a code fence.
You may find that reordering nodes and relationships gives a better overall
diagram.

```mermaid
flowchart LR
  UI[Your UI]
  API[Your API]

UI -->|UI calls API| API
API -.->|API responds| UI
```

Typically, I only show one side of this interaction to emphasize dependencies,
and reserve the back and forth for [_sequence
diagrams_](#simple-sequence-diagram-example):

```mermaid
flowchart LR
  UI[Your UI]
  API[Your API]

UI -->|UI calls API| API
```

If your interactions are multiple and complex, you can use [UNICODE "circled
digits"](https://graphemica.com/search?q=circled) to help the reader follow:

```mermaid
flowchart LR
  UI[Your UI]
  API[Your API]

UI -->|①<br>UI calls API| API
API -.->|②<br>API responds| UI
```

See [_A tip on special
characters_](Using-the-templates#a-tip-on-special-characters) for using 
"circled numbers" in diagrams.

## Simple sequence diagram example

Here is a simple sequence diagram with Mermaid.
You can embed this directly in your wiki documentation using a code fence.
You may find it more helpful to use sequence diagrams only for deep diving
into specific interactions;
some readers may find the level of detail overwhelming, and others will love
you for it.

```mermaid
sequenceDiagram
  UI ->>+ API: GET pizza status
  API -->>- UI: Here is the response body, such as "pizza still cooking"
```

Here is the same interaction but [with success/failure HTTP status
codes](https://mermaid.js.org/syntax/sequenceDiagram.html#alt):

```mermaid
sequenceDiagram
  UI ->>+ API: GET pizza status
  alt Status is 200
    API -->>- UI: Here is the response body, such as "pizza still cooking"
  else Status is 4xx or 5xx
    API -->> UI: Here is an error response body, such as "is this an open pizza order?" (404)
    API -->> UI: Here is an error response body, such as "oops! Please retry" (500)
  end
```

> [!NOTE]
> Mixing `+`/`-` to call out complete interactions does not work the same when
> using `alt` to show errors.
> You can only complete the interaction from one side of "alternatives";
> I typically pick the happy path for this, and call out sad paths as
> alternatives.

## Simple ERD diagram example

I typically use ERD diagrams to:

- Do the classic thing of describing SQL tables and their relationships
- Visually represent JSON to explain the properties

Here is a simple ERD diagram to represent JSON with Mermaid:

```mermaid
erDiagram
  PizzaPie {
    string pieId "each pie is unique (this is a UUID)"
    string orderTime "a timestamp in UTC"
    string comments "customer special requests"
  }

  OnionTopping {
    string pieId "refers to the pizza pie (this is a UUID)" 
    string toppingId "support multiple toppings including onions (this is a UUID)"
    string orderTime "a timestamp in UTC"
    string type "always 'ONIONS' for this topping"
    string color "one of: GREEN, RED, or WHITE"
    string style "one of: FRESH or GRILLED"
    string comments "customer special request"
  }
```

Here is the example expanded to show a SQL design:

```mermaid
erDiagram
  PIZZA_PIE {
    uuid PIE_ID PK "each pie is unique (for DBs not supporting UUID, a string)"
    timestamp ORDER_TIME "in UTC"
    string COMMENTS "customer special requests"
  }

  TOPPING_ONION {
    uuid PIE_ID FK "refers to the pizza pie; for DBs not supporting UUID, a string"
    uuid TOPPING_ID PK "support multiple toppings including onions; for DBs not supporting UUID, a string"
    timestamp ORDER_TIME "in UTC"
    text TOPPING_TYPE "always 'ONIONS' for this topping; some DBs support enums"
    text ONION_COLOR "one of: GREEN, RED, or WHITE; some DBs support enums"
    text ONION_STYLE "one of: FRESH or GRILLED; some DBs support enums"
    text ONION_COMMENTS "customer special requests"
  }

  PIZZA_PIE ||--o{ TOPPING_ONION: toppings
```

> [!TIP]
> You shoud update ERD diagrams to match the features in your database, such
> as support for UUIDs and timestamps (in UTC).

> [!TIP]
> See ["Relationship
> Syntax"](https://mermaid.js.org/syntax/entityRelationshipDiagram.html#relationship-syntax)
> in Mermaid for representing other entity or table relationships.
