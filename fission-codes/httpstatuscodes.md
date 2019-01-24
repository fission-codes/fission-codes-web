---
layout: default
parent: FISSION Codes
title: HTTP Status Codes
nav_order: 20
---

# HTTP Status Codes

The [Wikipedia list of HTTP Status Codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes) is a good resource, listing the ~75 or so codes -- both standards and "well known" usages.

With one byte, the [16x16 grid](grid of FISSION Codes) has lots of room to have semantics that are richer than those in HTTP.

HTTP Status Codes were defined as a section of the [HTTP/1.1 RFC2616](https://www.ietf.org/rfc/rfc2616.txt).

The W3C has a page which splits out the [Status Code Definitions](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html).

Today, HTTP Status Codes are split across multiple RFCs, with some status codes having their own RFC, e.g. [RFC7538 for status code 308, Permanent Redirect](https://tools.ietf.org/html/rfc7538).

The [Mozilla Developer Network explains `418 I'm a teapot`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/418):

> The HTTP `418 I'm a teapot` client error response code indicates that the server refuses to brew coffee because it is a teapot. This error is a reference of Hyper Text Coffee Pot Control Protocol which was an April Fools' joke in 1998.

A useful resource for browsing the codes is the [httpstatuses.com](https://httpstatuses.com/) site.