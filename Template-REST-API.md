* [Toppings](#toppings)
* [URL format and versioning](#url-format-and-versioning)
* [Response shapes](#response-shapes)

> [!TIP]
> It is best to start your documentation page with internal page links that
> let folks jump quickly to into your API (such as [Toppings](#toppings) later
> in this page).
> This helps them with navigation.

> [!NOTE]
> Another style than bullet points is sentences on separate lines such as:<br>
> _Jump to [Toppings](#toppings)._<br>
> _Jump to [URL format and versioning](#url-format-and-versioning)._<br>
> _Jump to [Success and failure responses](#response-shapes)_.
>
> You should select a style that best helps readers find information.

## Understanding this page

This page documents the REST API endpoints available for Toppings.
The endpoint documentation has technical details for you as the consumer of the API, and also additional information:
- How do you want to present your endpoints?
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
> These symbols are UNICODE characters pasted directly into this file.
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
|404 (Not Found)|A missing topping PIZZA-TOPPING-ID in the URL|
|422 (Unprocessable Content)|The values in the JSON body of a POST or PUT are invalid, or violate a business rule but the JSON is well-structured|
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

> [!IMPORTANT]
> You will want to give a top-level summary of your endpoints, but you may
> choose different styles or a combination depending on your intended
> audience.

> [!TIP]
> Present the same information as a list of questions above, and as a more
> detailed table below.
> It is more work for you as an author, but helps folks find information more
> quickly depending on their style of thinking.

|Purpose (click for details)|Client|REST call|JSON payloads|
|---------------------------|------|---------|-----------|
|✳️ [Create a new topping for a pie](#add-one-topping)|Pizza UI and **Onions team**|`POST /v1/api/pie/PIE-PIZZA-ID/topping`|`data` property has the [Pie JSON](Template-JSON-Models#pies) holding the new topping|
|✳️ [Edit an existing topping for a pie](#edit-one-topping)|Pizza UI and **Onions team**|`PUT /v1/api/pie/PIE-PIZZA-ID/topping/TOPPING-PIZZA-ID`|`data` property has the [Pie JSON](Template-JSON-Models#pies) holding the edited topping|
|✳️ [Delete an existing topping for a pie](#delete-one-topping)|Pizza UI and **Onions team**|`DELETE /v1/api/pie/PIE-PIZZA-ID/topping/TOPPING-PIZZA-ID`|`data` property has the [Pie JSON](Template-JSON-Models#pies) showing the topping is gone|

> [!NOTE]
> And after providing quick links for jumping to specific endpoints, then
> break down each endpoint with specifics in a standard format.
> This is a tabular format more suitable for programmers.

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

> [!CAUTION]
> This is an example "caution" note for an endpoint:
> _This call sends an update to the message bus reflecting the change to a
> pizza pie with changed toppings._

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

- `PIZZA-PIE-ID` &mdash; the `pizzaId` property of the pie; example: a UUID
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

- 201 (Created) &mdash; The new topping is created
- 404 (Not found) &mdash; The pie PIZZA-ID is not currently available
- 422 (Unprocessable content) &mdash; The topping violates business rules;
   your posted JSON is fine, but there is something wrong in the values

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

- `PIZZA-PIE-ID` &mdash; the `pizzaId` of the pie; example: a UUID provided by
  Pizza
- `PIZZA-TOPPING-ID` &mdash; the `pizzaId` of the topping; example a UUID
  provided by Pizza

> [!NOTE]
> This is an example of multiple placeholders in the URL.

#### Request body

The body is a [Topping JSON](Template-JSON-Models#toppings) object.

#### Response body

The response body has in the `data` property
[pie subgraph JSON](Template-JSON-Models#pies) for the pie
identified as `PIE-PIZZA-ID`.

#### Status codes

- 200 (OK) &mdash; The existing topping is edited
- 404 (Not found) &mdash; The pie PIZZA-ID is not currently available
- 404 (Not found) &mdash; The topping PIZZA-ID is not currently available

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

- `PIZZA-PIE-ID` &mdash; the `pizzaId` property of the pie; example: a
  UUID provided by Topping
- `PIZZA-TOPPING-ID` &mdash; the `pizzaId` of the topping; example a UUID
  provided by Topping

#### Response body

The response body has in the `data` property
[pie subgraph JSON](Template-JSON-Models#pies) for the pie
identified as `PIE-PIZZA-ID`.

#### Status codes

- 200 (OK) &mdash; The topping is gone
- 404 (Not found) &mdash; The pie PIZZA-ID is not currently available
- 404 (Not found) &mdash; The topping PIZZA-TOPPING-ID is not currently
  available

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
    "apiVersion": "v1", // Make it easier to see your API versioning
    "status": "success", // Make it easier to filter responses
    // A timestamp for this REST response; something a consumer can save or use
    "effectiveTime": "1970-01-01T00:00:00.000000Z",
    "data": { } // or [ ] depending on the endpoint 
}
```

> [!NOTE]
> Here "effectiveTime" is specific to the Pizza API.
> For your API, you might provide similar suitable metadata, or none at all
> depending your needs.
> A common choice (not shown here) is to include a timestamp of when you
> API was called; this aids in debugging.
> comments and is visually the same when rendered.

### Error payloads

Each error payload provides structured error payloads:

```javascript
{
    "apiVersion": "v1", // Make it easier to see your API versioning
    "status": "error", // Make it easier to filter responses
    "code": 599, // Same as the HTTP status code
    "reason": "Today is too hot to work",
    "effectiveTime": "1970-01-01T00:00:00.000000Z"
}
```

> [!NOTE]
> The error payload (the response body in HTTP) can be plain text (not
> processible by systems, but good for humans), or a JSON body following
> agreed conventions as shown above (processible in software by callers).
> Using a JSON body for error is _particularly_ helpful as a remote UI can
> scan for the error cause, and provide a human message specific for their
> users, and log aggregation downstream can better filter.
>
> Whatever you select, ensure you provide an appropriate HTTP `Content-Type`
> header in the responses from your API.

> [!NOTE]
> Note that for 404 (Not found) responses it is helpful to include a
> human-readable message in the body indicating that the URL format is OK, but
> that the `PIZZA-ID` or `PIZZA-TOPING-ID` does not match an existing pie or
> topping.
> This helps distinguish between a badly-formed URL and a missing resource.

> [!TIP]
> There are a lot of approaches to handling error conditions in the JSON
> response to callers.
> One is [RFC 7807 &mdash; _Problem Details for HTTP
> APIs_](https://datatracker.ietf.org/doc/html/rfc7807).
> Your REST API should decide on how to represent errors: the key point is
> that you do have an agreement shared with API consumers on how to do so.
