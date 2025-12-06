# Movie Database

## API Overview
Movie Database is a collection of information for movies, tv-shows, actors.

Includes youtube trailer url, awards, full biography, and many other usefull informations. This api provides complete and updated data for over 9 million titles ( movies, series and episodes) and 11 million actors/crew and cast members.



## Available Endpoints

Every endpoint returns and object with 'results' key. Endpoints with pages has additional keys -> 'page', 'next', 'entries'

1. **Titles**
    - **Dath:** /titles
    - **Description:** Returns array of titles according to filters / sorting query parameters provided
    - **query parameters:** multiple, unique query parameter 'list' that sets the collection you want to query - options available in Utils - Titles Lists
    - **model:** title

2. **Actors**
    - **path:** /actors
    - **description:** returns array of actors according to filters provided
    - **query parameters:** limit, page
    - **model:** actor



## Request and Response Format

This is a sample of Raw Request for movie titles:

```
    GET https://moviesdatabase.p.rapidapi.com/titles HTTP/1.1
    access-control-allow-credentials: true
    access-control-allow-origin: *
    content-length: 7014
    content-security-policy: default-src 'self';base-uri 'self';block-all-mixed-content;font-src 'self' https: data:;frame-ancestors 'self';img-src 'self' data:;object-src 'none';script-src 'self';script-src-attr 'none';style-src 'self' https: 'unsafe-inline';upgrade-insecure-requests
    content-type: application/json; charset=utf-8
    date: Sat, 06 Dec 2025 13:51:12 GMT
    etag: W/"1b66-/3sXRdwO/RH5anZGQUSTNF1+NEI"
    expect-ct: max-age=0
    referrer-policy: no-referrer
    server: RapidAPI-1.2.8
    strict-transport-security: max-age=15552000; includeSubDomains
    x-content-type-options: nosniff
    x-dns-prefetch-control: off
    x-download-options: noopen
    x-frame-options: SAMEORIGIN
    x-permitted-cross-domain-policies: none
    x-rapidapi-region: AWS - eu-central-1
    x-rapidapi-request-id: c943f34f837238c8b320ea4efde7b8e9ce1dd49328908a9bb11d66bda08ae711
    x-rapidapi-version: 1.2.8
    x-ratelimit-rapid-free-plans-hard-limit-limit: 500000
    x-ratelimit-rapid-free-plans-hard-limit-remaining: 499999
    x-ratelimit-rapid-free-plans-hard-limit-reset: 2678333
    x-xss-protection: 0
    specificMethodHeaders: [object Object]
```


This is a sample Response format:

```
    page:1
        next:"/titles?page=2"
        entries:10
        results:0:
        _id:"61e57fd65c5338f43c777f4a"
        id:"tt0000081"
        primaryImage:
        id:"rm211543552"
        width:226
        height:300
        url:"https://m.media-amazon.com/images/M/@._V1_.jpg"
```


## Authentication

RapidAPI uses API key–based authentication, where your API key must be included in every request you send.

1. Subscribe to the API
2. Get your X-RapidAPI-Key
3. Send a request including:
    - X-RapidAPI-Key: <your key>
    - X-RapidAPI-Host: <api hostname>
4. RapidAPI verifies → forwards → returns JSON
5. You consume the response

## Error Handling
Here are the most common errors you will encounter when calling a Movie Database API on RapidAPI—along with why they happen and how to handle them cleanly in your application.

1. **400 — Bad Request**
    Returned when the request is malformed or required query parameters are missing.

    **Example Causes**
    - Missing search query (q, query, etc.)
    - Invalid movie ID format
    - Unsupported parameter types

    **Recommended Handling**
    - Validate inputs before sending the request.
    - Provide helpful feedback to users.


2. **404 — Not Found**
Requested resource or endpoint does not exist.

    **Example Causes**
    - Mistyped endpoint path.
    - Movie ID not found.
    - Invalid URL format.

    **Recommended Handling**
    - Verify the endpoint path.
    - If a user searched for unavailable content:
        - “No results found for your search.”


3. **500 — Internal Server Error**
Indicates a problem on the API provider’s side.

    **Example Causes**
    - Provider malfunction
    - Unexpected behavior inside the API
    - RapidAPI internal failure

    **Recommended Handling**
    - Retry after a short delay.
    - Log the error for debugging.
    - Show fallback message:


## Usage Limits and Best Practices
Usage limits depend on the subscription plan selected in RapidAPI (Free, Basic, Pro, Ultra, etc.). Each plan defines how many requests you can make within a specific time period.

1. **How Rate Limits Work**
- Every request you make counts toward your quota.
- Exceeding limits returns HTTP 429 (Too Many Requests).
- Limits reset at the start of each new billing cycle.

2. **Best Practices**
- Implement caching
- Debounce user inputs
- Validate inputs before sending Requests
