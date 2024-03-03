> Welcome to the wiki-docs wiki!

The above is the default starting content when you use the "wiki" feature in
GitHub.

If your GitHub project does not yet have a wiki, go to the "Wiki" option in
the GitHub UI for your project (it appears in the top navigation bar) and
create the default first page.

## Sample wiki pages

### Documenting your REST API calls

Start with these two pages in your wiki to document REST endpoints and JSON
content, and edit as needed:

* [[Template REST API]] &mdash; document your REST endpoints
* [[Template JSON Models]] &mdash; document your JSON payloads

You will rename these to remove the "Template" prefixes, and can provide your
readers with "REST API" and "JSON Models" wiki documentation pages.

### Diagramming your architecture

## Working with the wiki locally on your machine

You can clone your wiki: it is a repo in GitHub.

For this project, the clone URL is:
`git@github.com:binkley/wiki-docs.wiki.git`.<br/>
Note the ".wiki" added after your code repo URL.
(See [Cloning wikis to your
computer](https://docs.github.com/en/communities/documenting-your-project-with-wikis/adding-or-editing-wiki-pages#cloning-wikis-to-your-computer).)

I like to edit the wiki locally, and take advantage of my IDE (such as
[IntelliJ](https://www.jetbrains.com/help/idea/markdown.html) or
[VSCode](https://code.visualstudio.com/docs/languages/markdown)) and the
command line, but it is up to you what works best.

### Commit messages

When you edit in the GitHub UI, the default commit message look like:

> Updated Home (markdown)

You can give a commit message in the UI at the bottom of the page:<br/>
![image](https://github.com/binkley/wiki-docs/assets/186421/e6ec089f-cc8e-4ab6-843a-a2daeacf41fa)

And you can always give a meaningful commit message when working locally with
`git commit -m <your message>` (and then pushing your change).

## Adding images and screenshots

I add images by editing with the GitHub UI for the wiki and pasting.
The UI automatically uploads the image, and inserts a link for you.

> [!NOTE]
> I am unsure how to do this locally with the cloned repo.
> The "assets" (images) are not part of cloning the wiki.

## The right-hand navigation sidebar

You may want to organize your wiki documentation pages.
GitHub lets you do this by customizing the right-hand navigation _Sidebar_
that appears in the GitHub UI.

To edit the Sidebar in the GitHub UI, use the "crayon" icon:<br/>
![image](https://github.com/binkley/wiki-docs/assets/186421/9e4c088f-3aef-42ca-b137-e769d65a0872)

If you customize the sidebar, readers can still find all pages&mdash;even
those you did not list:<br/>
![image](https://github.com/binkley/wiki-docs/assets/186421/decb1b18-0318-44d2-bb39-d48c9aa8a570)

Locally the right-hand navigation sidebar is the `_Sidebar.md` file in your
wiki repo clone.
