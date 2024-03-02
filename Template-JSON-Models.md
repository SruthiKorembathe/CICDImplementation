## Instructions

_Why documentation like this?_

This pulls togeter conversations you have with consumers of your API and JSON.
If you have _one consumer only_, it may not be worth effort to document;
however, you may find that you get a later second, or third consumer, and
then you repeat the same conversations.
Your documentation builds _informed consumers_ who skip the easy questions,
and ask more interesting ones.

This template uses for examples only this portion:

* Pie JSON
* Topping JSON

The full set of JSON Models has more types of JSON, but I want this template
to focus on what is needed for the [template API](Template-REST-API).

To use the template in your data product documentation, you will:
- Remove this _Instructions_ section after you are done with it.
- Remove _notes_ and _tips_ sections that are about editing your copy of this
   template.
   You will add your own _notes_ and _tips_ sections relevant to your JSON
   (and possibly similar callouts).

Throughout the template, I'll call out _notes_ and _tips_ like this:

> [!NOTE]
> Here is the first note.<br>
> Note that this is how notes look like.<br>
> You can read more on how callout-style remarks look in GitHub markdown here:
> [_...highlight a "Note" and "Warning..."_](https://github.com/orgs/community/discussions/16925).
> Full options for markdown in your documentation include as part of
> `[!style]` where "style" is one of:
> - `NOTE` &mdash; used in this template
> - `TIP` &mdash; used in this template
> - `IMPORTANT` &mdash; help consumers of the JSON to success
> - `WARNING` &mdash; the consumer of the JSON should get user intervention,
>   and possibly have additional user interaction to confirm impactful
>   permanent changes
> - `CAUTION` &mdash; talk about side effects or non-obvious behavior, but
>   usually does not require additional user interaction

> [!TIP]
> Here is the first tip.<br>
> You can edit your wiki documentation locally by cloning the wiki
> repository for your project.
> This lets you _use VSCode_ for editing if you prefer that over the web UI in
> GitHub.
>
> For example <https://github.com/ExxonMobil/pizza-pie-api.wiki> is the
> repo URL of the wiki for this file.
> **Note** the ".wiki" at the end of the code repo URL which tells GitHub that
> you are editing documentation and not the code.
>
> To edit this page locally, you would use `git clone` for the wiki repo, and
> work with `pull`, `commit`, and `push`.
> However, editing locally won't get you GitHub previews for your page.

When you are finished with these instructions, delete everything through the
`----` below, and any _note_ or _tip_ sections for these instructions.

You may want to take advantage of the formatting for notes and tips for your
own JSON consumers, especially if the JSON represents non-obvious behavior or
side effects, and any helpful remarks that should be called out.

> [!TIP]
> If you inspect the markdown for this template, you'll spot ` ```javascript `
> code fences.
> Technically the code blocks are JSON, however Javascript supports inline
> comments and is visually the same when rendered.

----

You will see JSON for Pizza in various contexts:

| JSON type | Context | Side effects | Impacts PSA dashboard |
|-----------|---------|--------------|-----------------------|
| [Pie](#pies) | Responses to calls for that alter toppings | All changes to pie context publish pie JSON to Service Bus.<br>Updates the `PIES` table in Snowflake, and views update | Yes |
| [Toppings](#toppings)<br>Each payload is for a specific topping type<br>(Or for DELETE is simply the URL) | Integrations post to Pizza API REST endpoint to change a specific topping. Pizza UI uses the same REST calls | All changes to pie context publish pie JSON to Service Bus.<br>Updates the affected "topping" tables in Snowflake (Onion, etc), and views update | Yes |

> [!NOTE]
> This table is an upfront way of setting expectations for your API consumers,
> and helps them jump to information quickly.

* [Toppings](#toppings) &mdash; Integrations post these to the Pizza API to
   change toppings. These are published back through Service Bus, and seen by
   all integrations and Snowflake &larr; **Integrations send these to the
   Pizza API to manage toppings** (Onions team); Pizza saves these to
   Snowflake tables
    - [Onion](#onions)

> [!NOTE]
> Here you break out the same information into shorter parts, again to ease
> understanding and to provide quick internal links.

## Published JSON

When sending JSON responses to API calls, or publishing to Service Bus, the
data payload should be wrapped JSON:

```javascript
{
    "apiVersion": "v1",
    "effectiveTime": "1970-01-01T00:00:00.000000Z", // "now"
    "data": { } // or [ ] depending on payload
}
```

> [!NOTE]
> See (Template-REST-API#response-shapes) for more details.

## Pies

In this template I omit the section on pie JSON as the REST API template
focuses on the topping endpoints, and not the pie endpoints.
Every change to toppings returns pie JSON to show the full context.

## Toppings

### Onions

| Purpose | Endpoints | Client |
|---------|-----------|--------|
| Express an Onion topping | Subpart of pie JSON | All integrations |
| | [Create](Template-REST-API#add-one-topping)/[edit](Template-REST-API#edit-one-topping)/[delete](Template-REST-API#delete-one-topping) one Onion topping | Pizza UI |

```javascript
{ 
    "startTime": "1970-01-01T00:00:00.000000Z",
    "pizzaId": "UUID", // Generated by Pizza
    "type": "Onion",
    "model": "STRING",
    "onionId1": "STRING",
    "onionId2": "STRING or null",
    "property": "STRING",
    "property2": "STRING or null",
    "equation": "STRING",
    "site": "STRING or null",
    "group": "STRING or null",
    "comments": "free text, else null"
}
```
