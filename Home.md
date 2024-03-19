> Welcome to the wiki-docs wiki!

The above is the default starting content when you use the "wiki" feature in
GitHub.

If your GitHub project does not yet have a wiki, go to the "Wiki" option in
the GitHub UI for your project (it appears midway in the top navigation bar)
and create the default first page.
If you do not see the "Wiki" option, you may need a project owner or
administrator to enable the option in "Settings | General":

![GitHub settings to enable a wiki](https://github.com/binkley/wiki-docs/assets/186421/8f75980b-84e3-41ad-aa7e-e5f1f1ac5f62 "GitHub settings to enable a wiki")

## Sample wiki pages

A good resource for getting started or exploring features available to you is
[Getting started with writing and formatting on
  GitHub](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github).

### Documenting your REST API calls

Start with these two pages in your wiki to document REST endpoints and JSON
content, and edit as needed:

* [[Template REST API]] &mdash; document your REST endpoints
* [[Template JSON Models]] &mdash; document your JSON payloads

You will rename these to remove the "Template" prefixes, and can provide your
readers with "REST API" and "JSON Models" wiki documentation pages.

### Diagramming your architecture

* [[Examples of diagramming]] &mdash; take advantage of Mermaid in your
  documentation

> [!NOTE]
> The above `[[Page Name]]` syntax uses GitHub markdown features (as does
> `[!NOTE]`).
> In vanilla Markdown the page links are:
> * [Template REST API](./Template-REST-API.md)
> * [Template JSON Models](./Template-JSON-Models.md)
> * [Examples of diagramming](./Examples-of-diagramming.md)

## Working with the wiki locally on your machine

You can _clone your wiki_: it is a repository in GitHub separate from your
code repository but attached to it in the GitHub UI.

For this project, the clone URL is:
`git@github.com:binkley/wiki-docs.wiki.git`.<br/>
Note the ".wiki" added after your code repo URL.
(See GitHub's [_Cloning wikis to your
computer_](https://docs.github.com/en/communities/documenting-your-project-with-wikis/adding-or-editing-wiki-pages#cloning-wikis-to-your-computer).)

I like to edit the wiki locally, and take advantage of my IDE (such as
[IntelliJ](https://www.jetbrains.com/help/idea/markdown.html) or
[VSCode](https://code.visualstudio.com/docs/languages/markdown)) and the
command line, but it is up to you what works best.
See [below](#adding-images-and-screenshots-to-a-wiki-page) for a case when to
switch back to the GitHub web UI.

### About commit messages

When you edit in the GitHub UI, the default commit message look like:

> Updated Home (markdown)

You can give a commit message in the UI at the bottom of the page:<br/>
![GitHub showing where you can have a Git commit message while using the UI](https://github.com/binkley/wiki-docs/assets/186421/e6ec089f-cc8e-4ab6-843a-a2daeacf41fa "GitHub showing where you can have a Git commit message while using the UI")

And you can always give a meaningful commit message when working locally with
`git commit -m <your message>` (and then pushing your change).

### Making the most of your editor

Most IDEs these days support Markdown, and several can show previews right in
the editor.
Below is not a comprehensive list, just those I've tried this with.

#### JetBrains

IntelliJ and the other JetBrains IDE products all support Markdown with
preview either out-of-the-box or with a free plugin download supported by
JetBrains.
Even nicer, JetBrains has a Mermaid (diagrams) plugin that seamlessly works
with the Markdown editor and with page preview.
Mermaid is the text-based diagramming tool used in GitHub wikis among other
places.

Here is a sample screenshot:

![Sample screenshot of Mermaid
plugin](https://github.com/binkley/wiki-docs/assets/186421/2c2cd321-fe83-439d-9db3-e98564609160
"Sample screenshot of Mermaid plugin")

## Adding images and screenshots to a wiki page

I add images by editing with the GitHub UI for the wiki and pasting directly
into the edit box.
The UI automatically uploads the image, and inserts a link for you.
There are examples throughout this wiki page.

### Avoiding web editing

I am unsure how to paste images locally into a wiki page with a cloned
repository.
The "assets" (images) created in the GitHub web UI are not part of cloning
your wiki.

However there is a perfectly good alternative: Add your image to your wiki
repository, and link directly with `![image](./filename.extension)`.
This also has the benefit of keeping your images as content in your source
control.

## Changing the right-hand navigation sidebar in GitHub UI

You may want to organize your wiki documentation pages.
GitHub lets you do this by customizing the right-hand navigation _Sidebar_
that appears in the GitHub UI.

To edit the Sidebar in the GitHub UI, use the "crayon" icon:<br/>
![Showing in GitHub how to edit the sidebar](https://github.com/binkley/wiki-docs/assets/186421/9e4c088f-3aef-42ca-b137-e769d65a0872 "Showing in GitHub how to edit the sidebar")

If you customize the sidebar, readers can still find all pages&mdash;even
those you did not list:<br/>
![Showing in GitHub how to find all pages when you have a custom sidebar](https://github.com/binkley/wiki-docs/assets/186421/decb1b18-0318-44d2-bb39-d48c9aa8a570 "Showing in GitHub how to find all pages when you have a custom sidebar")

Locally the right-hand navigation sidebar is the `_Sidebar.md` file in your
wiki repo clone.
