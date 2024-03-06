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

You may want to take advantage of the formatting for notes and tips for your
own API consumers, especially if an endpoint or set of endpoints with
non-obvious behavior or side effects, and any helpful remarks that should be
called out.

### JSON code with comments

When you inspect the markdown for templates, you'll spot ` ```javascript `
code fences.
Technically the code blocks are `json`, however `javascript` supports inline
comments for documentation:
JSON does not support comments but Javascript does.
This is a trick you may want to reuse.

## What again is this API?

What are "toppings" and "pies" and who is "Pizza"?
These are examples for the templates templates, and are about pizza pies and
the toppings on them.

> [!NOTE]
> I didn't tell you that up front, but you are clever and will figure it out.
