# Instructions

_Why documentation like this?_

This page pulls together conversations you have with consumers of your API and
JSON.
If you have _one consumer only_, it may not be worth effort to document;
however, you may find that you get a later second, or third consumer, and
then you repeat the same conversations.
Your documentation builds _informed consumers_ who skip the easy questions,
and ask more interesting ones.

This template uses a limited API that is part of a larger one:

* Pies &mdash; the larger API, not documented in the templates
* Toppings &mdash; a smaller API part of "Pizza", and documented

A full API has more collections of endpoints, for example _pies_ and not
just _toppings_, but I want this template to focus on one thing, and you can
add more.

To use the templates in your documentation, you will:
- Remove _notes_ and _tips_ sections that are about editing your copy of this
   template.
   You will add your own _notes_ and _tips_ sections relevant to your API (and
   possibly similar callouts).
- Update the names for collections of related endpoints.
   If your REST API does not have groupings of related endpoints, then this
   does not make sense; however, for more complex APIs, you may want to
   group endpoints together in the documentation.
- Update the JSON models that your REST API consumes or produces.
- Decide if you want higher-level explanatory sections&mdash;such as those on
   versioning&mdash;to be in another page, or perhaps these are not relevant.
   An example is explanatory materials that help your delivery team or API
   consumers understand your decisions for your API.

## Some wiki implementation details

### Notes, tips, all that

You should take advantage of notes, tips, and other options in your own API
documentation, especially if an endpoint for endpoints with non-obvious
behavior or side effects, and call out helpful remarks.

Throughout the templates, I'll call out _notes_ and _tips_ like this in the
Markdown code:

> [!NOTE]
> Here is the first note.<br>
> Note that this is how notes look like.<br>
> You can read more on how callout-style remarks look in GitHub Markdown here:
> [_...highlight a "Note" and "Warning..."_](https://github.com/orgs/community/discussions/16925).
> Full options for GitHub Markdown in your documentation include as part of
> `[!style]` where "style" is one of:
> - `NOTE` &mdash; used in this template
> - `TIP` &mdash; used in this template
> - `IMPORTANT` &mdash; help the API caller to success
> - `WARNING` &mdash; the API caller should get user intervention, and
>   possibly have additional user interaction to confirm impactful permanent
>   changes
> - `CAUTION` &mdash; talk about side effects or non-obvious behavior, but
>   usually does not require additional user interaction.
>   An example is a REST call that modifies a remote database visible to
>   others.

> [!TIP]
> Here is the first tip.<br>
> You can edit your wiki documentation locally by cloning the wiki
> repository for your project.
> This lets you _use VSCode_ for editing if you prefer that over the web UI in
> GitHub.
>
> For example <https://github.com/your-github-id-or-org/pizza-pie-api.wiki> is
> the repo URL of the wiki for this file.
> **Note** the ".wiki" at the end of the code repo URL which tells GitHub that
> you are editing documentation and not the code.
>
> To edit this page locally, you would use `git clone` for the wiki repo, and
> work with `pull`, `commit`, and `push`.
> However, editing locally won't get you GitHub previews for your page.

### Definition lists

Definition lists are one of my favorite HTML features, however they have no
native Markdown syntax without
[extensions](https://www.markdownguide.org/extended-syntax/#definition-lists).
Unfortunately these extensions are not supported in GitHub Markdown.

Workarounds:

- Use HTML directly in your Markdown for `<dl>`, `<dt>`, and `<dd>`.
   When using these, you may not use Markdown within the HTML section, and
   need to use HTML tags.
   Here is an example:
   <dl>
       <dt>Toppings</dt>
       <dd>These are delicious bits added to your pizza pie.<br/>
           Each topping gets a separate <code>PIZZA-TOPPING-ID</code>
           distinct from the pizza pie (<code>PIZZA-ID</code>).
       </dd>
   </dl>
- Fake the defintion list which is what I've done in these templates.
   So I use a bullet list, and the `&mdash;` character (&mdash;) to describe
   lists that would be nicer done with HTML definition lists.
   In Markdown the above example would looks like:
   - **Toppings** &mdash; These are delicious bits added to your pizza
     pie.<br>
     Each topping gets a separate `PIZZA-TOPPING-ID` distinct from the pizza
     pie (`PIZZA-ID`).

### JSON code with comments

When you inspect the GitHub Markdown for templates, you'll spot `
```javascript ` code fences.
Technically the code blocks are `json`, however `javascript` supports inline
comments for documentation:
JSON does not support comments but Javascript does.<br>
_This is a trick you may want to reuse._

An example with `json` as the code fence language (` ```json `):
```json
{
   "bob": "Marley" // there are many Bobs in the world, this is just one
}
```
And the same with `javascript` as the code fence language (` ```javascript `):
```javascript
{
   "bob": "Marley" // there are many Bobs in the world, this is just one
}
```

## What again is this API?

What are "toppings" and "pies" and who is "Pizza"?
These are examples for the templates templates, and are about pizza pies and
the toppings on them.

> [!NOTE]
> I didn't tell you that up front, but you are clever and will figure it out.
