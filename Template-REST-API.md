## Instructions

_Why documentation like this?_

This page pulls together conversations you have with consumers of your API and
JSON.
If you have _one consumer only_, it may not be worth effort to document;
however, you may find that you get a later second, or third consumer, and
then you repeat the same conversations.
Your documentation builds _informed consumers_ who skip the easy questions,
and ask more interesting ones.

This template uses a limited API that is part of a larger one:

* Toppings

A full API has more collections of endpoints, for example _pies_ and not
just _toppings_, but I want this template to focus on one thing, and you can
add more.

To use the template in your data product documentation, you will:
- Remove this _Instructions_ section after you are done with it.
- Remove _notes_ and _tips_ sections that are about editing your copy of this
   template.
   You will add your own _notes_ and _tips_ sections relevant to your API (and
   possibly similar callouts).
- Update the names for collections of related endpoints.
   If your REST API does not have groupings of related endpoints, then this
   does not make sense; however, for more complex APIs, you may want to
   group endpoints together in the documentation.
- Decide if you want higher-level explanatory sections such as those on
   versioning to be in another page, or perhaps these are not relevant.
   An example is explanatory materials that help your delivery team or API
   consumers understand your decisions on your API.

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
>   usually does not require additional user interaction

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

When you are finished with these instructions, delete everything through the
`----` below, and any _note_ or _tip_ sections for these instructions.

You may want to take advantage of the formatting for notes and tips for your
own API consumers, especially if an endpoint or set of endpoints with
non-obvious behavior or side effects, and any helpful remarks that should be
called out.

(What are "toppings" and "pies" and who is "Pizza"?
These templates are about pizza pies and the toppings on them.
I didn't tell you that up front, but you are clever and will figure it out.)

----

* [Toppings](#toppings)
* [URL format and versioning](#url-format-and-versioning)
* [Response shapes](#response-shapes)

> [!NOTE]
> "Toppings" is the main API for this template documentation.<br>
> "URL format and versioning" is helpful to give API consumers an overall
> picture of what your API paths look like.<br>
> "Response shapes" talks about your success and failure responses.
> I don't show the APIs for Pizza or pies.

> [!TIP]
> It is best to start your documentation page with curated internal links that
> help folks jump quickly to those parts of your API that interests them (such
> as [Toppings](#toppings) later in this page).
> This helps with navigation.

> Another style is with sentences rather than bullet lists, such as:<br>
> _Jump to [Toppings](#toppings)._<br>
> _Jump to [URL format and versioning](#url-format-and-versioning)._<br>
> _Jump to [Success and failure responses](#response-shapes)_.<br>
> This is up to you to pick a good style at the top of your page than best
> helps readers to quickly find what they want.

## Understanding this page

This page documents the REST API endpoints available for Toppings.
The endpoint documentation has technical details for you as the consumer of the API, and also additional information:
- What is the delivery status of an endpoint? Can I use this now?
- What side effects or complications might impact me?

### Endpoints are marked for their status

- ✳️ fully implemented and should just work (all uses unless noted)
- ✴️ implemented but with limitations (see endpoint description)
- ䷴ development in progress (DEV or ACC may work for you, but not ready for PRD; talk with the team for details)
- ⛔ not yet implemented but planned (upcoming work; an FYI to help you plan your integration with us)

> [!NOTE]
> These are simple markers of the development status of each endpoint.
> This helps API consumers know which endpoints are ready for use, and in what
> environments they may call them.
> For in progress or planned work, these help planning for upcoming
> integration work.

> [!NOTE]
> These symbols are UNICODE characters pasted directly into this markdown.
> Graphemica is a great site for finding suitable UNICODE, for example the
> [✳️ ](https://graphemica.com/%E2%9C%B3) above.

### Responses for all API calls

This is a general summary for HTTP response status codes.

|Status return|Description|
|-------------|-----------|
|200 (OK)|Success for a GET, PUT, or DELETE|
|201 (Created)|Success for a POST|
|400 (Bad Request)|Syntax error with the JSON body of a POST or PUT|
|400 (Bad Request)|Bad query parameters|
|401 (Unauthorized)|User or app client did not authorize, or the credentials are invalid|
|403 (Forbidden)|Caller credentials are OK, but they are not in the right AD groups|
|404 (Not Found)|Invalid URL path, recheck the REST API documentation|
|404 (Not Found)|An invalid site acronym in the URL|
|404 (Not Found)|A missing pie PIZZA-ID in the URL|
|404 (Not Found)|A missing topping PIZZA-ID in the URL|
|422 (Unprocessable Content)|The values in the JSON body of a POST or PUT are invalid, or violate a business rule|
|429 (Too Many Requests)|We many need to adjust our Cosmos scaling|

> [!NOTE]
> It helps to provide a summary table of HTTP status codes for your API, in
> addition to specific details for each endpoint.
> Some of these may not apply to your data product, for example 429 related
> to the Azure Cosmos Gremlin DB.
> However, you should provide a general table like this to help with
> validation so that testing your API can give feedback on what works and what
> does not work when calling your API.

## Toppings

> [!NOTE]
> This is the meat of the documentation.
> This is where documentation readers can learn what endpoints of yours they
> want to call.

* ✳️ [I want to add a new topping to a pie](#add-one-topping)
* ✳️ [I want to edit an existing topping for a pie](#edit-one-topping)
* ✳️ [I want to delete an existing topping for a pie](#delete-one-topping)

> [!TIP]
> Present the same information as a list of questions above, and as a more
> detailed table below.
> It is more work for you as an author, but helps folks find information more
> quickly depending on their style of thinking.

|Purpose (click for details)|Client|REST call|Description|
|---------------------------|------|---------|-----------|
|✳️ [Create a new topping for a pie](#add-one-topping)|Pizza UI and **Onions team**|`POST /v1/api/pie/PIE-PIZZA-ID/topping`|`data` property has the [Pie JSON](Template-JSON-Models#pies) holding the new topping|
|✳️ [Edit an existing topping for a pie](#edit-one-topping)|Pizza UI and **Onions team**|`PUT /v1/api/pie/PIE-PIZZA-ID/topping/TOPPING-PIZZA-ID`|`data` property has the [Pie JSON](Template-JSON-Models#pies) holding the edited topping|
|✳️ [Delete an existing topping for a pie](#delete-one-topping)|Pizza UI and **Onions team**|`DELETE /v1/api/pie/PIE-PIZZA-ID/topping/TOPPING-PIZZA-ID`|`data` property has the [Pie JSON](Template-JSON-Models#pies) showing the topping is gone|

> [!NOTE]
> And after providing quick links for jumping to specific endpoints, then
> break down each endpoint with specifics in a standard format.

### Add one topping

> [!NOTE]
> This is an example of a fully documented endpoint with remarks in the
> template of things you should document or consider.

**Public**.

> [!NOTE]
> Please mark each endpoint as either **Public** or **Internal**.
> You have two audiences:
> * Your own devivery team who would use the internal endpoints
> * Your API consumers who would only use the public endpoints
> Marking in this way help API consumers ignore internal endpoints.

✳️ `POST /v1/api/pie/PIZZA-PIE-ID/topping`

> [!NOTE]
> A one-line usage for the endpoint together with a marker on its development
> status.
> This helps API consumers know which endpoints are ready for use, and helps
> the delivery team see which endpoints are in progress or upcoming for work.
> It also gives a "preview" to API consumers of what endpoints may be
> available in the future.

> [!TIP]
> Be consistent in your formatting for which parts of a URL are literal
> text, and which part are placeholders (URL path pies).
> In the above endpoint, "PIE-PIZZA-ID" is a placeholder.

#### Limitations

- The API rejects multiple toppings of the same "type" and "subtype".
   This means for pies:
   - Only one Onion topping for a pie

> [!NOTE]
> This endpoint has additional information about side effects that your
> consumer will want to understand.
> Consider using either a section like this, or calling concerns out in
> [`WARNING` blocks](https://github.com/orgs/community/discussions/16925).

#### URL parameters

- `PIZZA-PIE-ID` -- the `pizzaId` property of the pie; example: a UUID
  provided by Pizza

> [!NOTE]
> And now you document each placeholder.

#### Request body

The body is a [Topping JSON](Template-JSON-Models#toppings) object.

> [!NOTE]
> And now you document any request body for the endpoint, typically only
> needed for POST and PUT calls.
> This is also a good place to link from your API documention to your JSON
> documentation.

#### Response body

The response body has in the `data` property
[pie subgraph JSON](Template-JSON-Models#pies) for the pie
identified as `PIE-PIZZA-ID`.

> [!NOTE]
> And now you document the response body for the endpoint, if any.
> For example all GET calls should have a response body, and few or no
> DELETE calls have one (except to return an error message).
> This is also a good place to link from your API documention to your JSON
> documentation.

#### Status codes

- 201 (Created) - The new topping is created
- 404 (Not found) - The site acronym is invalid
- 404 (Not found) - The pie PIZZA-ID is invalid
- 422 (Unprocessable content) - The topping violates business rules

> [!NOTE]
> Conclude documenting an endpoint with a list of possible HTTP status codes
> for the response, and explanation how callers might correct errors.

----

> [!TIP]
> See the page break ("horizontal rule" in HTML-speak) above?
> Since the information for each endpoint is quite dense, it greatly aids the
> eye scanning down the page to see each endpoint visually separated with a
> strong break.

### Edit one topping

**Public**.

✳️ `PUT /v1/api/pie/PIZZA-PIE-ID/topping/PIZZA-TOPPING-ID`

#### URL pies

- `PIZZA-PIE-ID` -- the `pizzaId` of the pie; example: a UUID provided by
  Pizza
- `PIZZA-TOPPING-ID` -- the `pizzaId` of the topping; example a UUID provided
  by Pizza

> [!NOTE]
> This is an example of multiple placeholders in the URL.

#### Request body

The body is a [Topping JSON](Template-JSON-Models#toppings) object.

#### Response body

The response body has in the `data` property
[pie subgraph JSON](Template-JSON-Models#pies) for the pie
identified as `PIE-PIZZA-ID`.

#### Status codes

- 200 (OK) - The existing topping is edited
- 404 (Not found) - The site acronym is invalid
- 404 (Not found) - The pie PIZZA-ID is invalid
- 404 (Not found) - The topping PIZZA-ID is invalid

----

### Delete one topping

**Public**.

✳️ `DELETE /v1/api/pie/PIZZA-PIE-ID/topping/PIZZA-TOPPING-ID`

#### Limitations

- Presently the API does not provide history or "soft delete".
   This operation is permanent.

> [!NOTE]
> This endpoint has additional information about side effects that your
> consumer will want to understand.
> An alternative way to present this is with a `> [!CAUTION` block.

#### URL pies

- `PIZZA-PIE-ID` -- the `pizzaId` property of the pie; example: a
  UUID provided by Topping
- `PIZZA-TOPPING-ID` -- the `pizzaId` of the topping; example a UUID provided
  by Topping

#### Response body

The response body has in the `data` property
[pie subgraph JSON](Template-JSON-Models#pies) for the pie
identified as `PIE-PIZZA-ID`.

#### Status codes

- 200 (OK) - The topping is gone
- 404 (Not found) - The site acronym is invalid
- 404 (Not found) - The pie PIZZA-ID is invalid
- 404 (Not found) - The topping PIZZA-ID is invalid

----

## URL format and versioning

All endpoints are rooted in a Pizza API version to provide a
backwards/forwards-compatible path for updating the API without coupling
clients to our schedule:

`/v1/the/rest/of/the/path`

See <https://dev.azure.com/EM-UIT/Portfolio-EMTEC/_wiki/wikis/Portfolio-EMTEC.wiki/17665/Version-REST-APIs> for discussion.

> [!NOTE]
> This is an important aspect of API design.
> There are several ways to version your API, and this example uses one of
> the simplest approaches: include the version at the start of the URL path.
> You may find that you will never support both older and newer clients,
> and versioning would not matter.
> However, predicting the future is tough (why your-github-id-or-org pays Economists
> well), so it usually pays off to prepare for versioning from the start of
> an API.

## Response shapes

The key JSON property in a response payload is `data` on success.

### Success payloads

Each success payload carries a JSON model in the `data` property:

```javascript
{
    "apiVersion": "v1",
    "status": "success",
    "effectiveTime": "1970-01-01T00:00:00.000000Z",
    "data": { } // or [ ] depending on endpoint 
}
```

> [!NOTE]
> Here "effectiveTime" is specific to the Pizza API.
> For your API, you might provide similar suitable metadata, or none at all
> depending your needs.
> A common choice (not shown here) is to include a timestamp of when you
> API was called; this aids in debugging.

> [!TIP]
> Notice that the API version is part of the response body, and not just the
> request URL path.
> This redundancy is helpful, especially for other consumers downstream from
> your direct API consumer, and helps with debugging.

> [!TIP]
> If you inspect the markdown for this template, you'll spot ` ```javascript `
> code fences.
> Technically the code blocks are JSON, however Javascript supports inline
> comments and is visually the same when rendered.

### Error payloads

Each error payload provides structured error payloads:

```javascript
{
    "apiVersion": "v1",
    "status": "error",
    "code": 599, // Same as the status code
    "reason": "Today is too hot to work"
}
```

> [!NOTE]
> The same comment about decorating the response body with metadata applies
> also to error responses, and not just to success responses.

> [!TIP]
> And having a separately defined, but standard, error response body helps
> callers with a consistent experience using your API.
> Again notice the redundancy, here not just with versioning, but with the
> HTTP status code in the response.

> [!NOTE]
> The below "note" is plain text in the original Pizza API documentation.
> While writing this template, it occured to me that I missed an opportunity
> to use the "NOTE" markdown like I am doing here in this note.

Note that for a 404 (Not found) it is helpful to include a message in the
body indicating that the URL format is OK, but that the `PIZZA-ID` does not
match an existing pie.
This helps distinguish between a badly-formed URL and a missing resource.

The message can be plain text, or an error code, or both.
