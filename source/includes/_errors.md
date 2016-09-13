# Errors

<aside class="notice">This error section is stored in a separate file in `includes/_errors.md`. Slate allows you to optionally separate out your docs into many files...just save them to the `includes` folder and add them to the top of your `index.md`'s frontmatter. Files are included in the order listed.</aside>

The Kittn API uses the following error codes:


Error Code | Meaning
---------- | -------
200 OK | Successful API request.
201 Created | The request has been fulfilled and a new resource has been created.
400 Bad Request | The request cannot be fulfilled due to bad syntax.
401 Unauthorized | Authentication is required and has not been provided or has failed.
403 Forbidden | The request was a valid request but the server is refusing to respond to it.
404 Not Found | The requested resource could not be found but could be available again in the future.
405 Method Not Allowed | A request was made of a resource using a method that is not accepted by that resource. For example, using a GET request when it should be a POST.
406 Not Acceptable | The requested resource is only capable of generating content not acceptable according to the Accept headers sent in the request.
411 Length Required | The request did not specify the length of the content, which is required by the requested resource.
422 Unprocessable Entity | The request was well-formed but there was some semantic errors.
500, 501, 502 | Shopify Server Errors.
503 Service Unavailable | The server is currently unavailable (because it is overloaded or down for service). If you reach your API limits you will receive this error.
