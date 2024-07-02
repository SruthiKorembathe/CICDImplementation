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

> [!CAUTION]
> Use of GitHub's markdown for "notes" and so forth work in a repo
> `README.md`, in wiki pages, but does not work is some other contexts.
> You need to try them yourself, and see what works and does not.

Throughout the templates, I'll call out _notes_ and _tips_ like this in the
Markdown code:

> [!NOTE]
> Here is the first note.<br>
> Note that this is how notes look like.<br>
> You can read more on how callout-style remarks look in GitHub Markdown here:
> [_...highlight a "Note" and "Warning..."_](https://github.com/orgs/community/discussions/16925).
> Full options for GitHub Markdown in your documentation include as part of
> `[!STYLE]` where "STYLE" is one of:
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
> (See [[Working with the GitHub wiki]].)
>
> For example <https://github.com/your-github-id-or-org/pizza-pie-api.wiki> is
> the repo URL of the wiki for this file.
> **Note** the ".wiki" at the end of the code repo URL which tells GitHub that
> you are editing documentation and not the code.
>
> To edit this page locally, you would use `git clone` for the wiki repo, and
> work with `pull`, `commit`, and `push`.
> However, editing locally won't get you GitHub previews for your page 
> without [plugins for your
> editor](working-with-the-github-wiki#making-the-most-of-your-editor).

#### A tip on special characters

> [!TIP]
> Here is another tip useful for any wiki editing:
> UNICODE charaters are supported in GitHub and most editors.
> In GitHub wiki text and diagrams (including Mermaid) you may want to show
> characters difficult to type but available in UNICODE.
>
> An example is [① (circle 1)](https://graphemica.com/%E2%91%A0), and
> progressing to 2 (②), 3 (③), etc.
> (I use these in diagrams to highlight flow sequence.)
>
> There are other excellent characters you can paste directly into your wiki
> such as ["point up"](https://graphemica.com/%E2%98%9D) or
> ["tada"](https://graphemica.com/%F0%9F%8E%89).
> Typically your browser shows a copy/pasteable character in the URL bar for
> [Graphemica](https://graphemica.com).

### Definition lists

Definition lists are one of my favorite HTML features, however they have no
native Markdown syntax without
[extensions](https://www.markdownguide.org/extended-syntax/#definition-lists).
Unfortunately these extensions are not supported in GitHub Markdown.

Workarounds:

- _Use HTML directly in your Markdown_ for `<dl>`, `<dt>`, and `<dd>`.
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
- _Fake the defintion list_ which is what I've done in these templates.
   So I use a bullet list, and the `&mdash;` character (&mdash;) to describe
   lists that would be nicer done with HTML definition lists.
   In Markdown the above example would looks like:

   - **Toppings** &mdash; These are delicious bits added to your pizza
     pie.<br>
     Each topping gets a separate `PIZZA-TOPPING-ID` distinct from the pizza
     pie (`PIZZA-ID`).

### JSON code with comments

When you inspect the GitHub Markdown for templates, you'll spot `
```javascript` code fences.
Technically the code blocks are `json`, however `javascript` supports inline
comments for documentation:
JSON does not support comments but Javascript does.<br>
_This is a trick you may want to reuse._

An example with `json` as the code fence language (` ```json`):
```json
{
   "bob": "Marley" // there are many Bobs in the world, this is just one
}
```
And the same with `javascript` as the code fence language (` ```javascript`):
```javascript
{
   "bob": "Marley" // there are many Bobs in the world, this is just one
}
```

## What again is this API and wiki docs?

What are "toppings" and "pies", and who is "Pizza"?
These are examples for REST API GitHub Markdown wiki documents, and are about
pizza pies and the toppings on them.

> [!NOTE]
> I didn't tell you that up front, but you are clever and will figure it out.
> Your own wiki docs should provide an upfront overview in the Home page to
> guide readers to what matters to them.
> I am using "pizza" and "pie" and "toppings" as examples.

A recommended source guiding you to a strong project README is [from Yegor
Bugayenko (Его́р
Бугае́нко)](https://www.yegor256.com/2019/04/23/elegant-readme.html).
Your wiki docs are **not the same** as your `README.md` in each of your
project's root repository!
But your README should point the reader to the wiki docs.

These templates are built from internal documentation at a global company
wanting better communication across their projects, and to help integrations
against their REST APIs.

They are sanitized for your protection (really mine).
