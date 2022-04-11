# URL

This page contains an overview of all possible error types inside the `https://api.publiq.be/probs/url/` namespace that can be returned by publiq's APIs.

> APIs can also use their own types for errors. The types below are used in situations where an API has no specific type for an error related to a the requested URL.

## not-found

*   **Type:** `https://api.publiq.be/probs/url/not-found`
*   **Title**: `URL not found`
*   **Status**: `404`

The URL you requested is not available. Possible causes include:

*   The endpoint does not exist
*   An id or slug of a resource in the path does not exist or is invalid

## query-parameter-missing

*   **Type:** `https://api.publiq.be/probs/url/query-parameter-missing`
*   **Title**: `Query parameter missing`
*   **Status**: `404`

A required query parameter is missing. More info on what parameter specifically can be found in the `detail` property of the response.

## query-parameter-invalid

*   **Type:** `https://api.publiq.be/probs/url/query-parameter-invalid`
*   **Title**: `Query parameter invalid`
*   **Status**: `404`

The value of a given query parameter is invalid. More info on what parameter specifically can be found in the `detail` property of the response.

Also used when a query parameter references another resource and that resource is not found.

In some cases, depending on the API, this can also be returned when an invalid parameter name is used.

## path-parameter-invalid

*   **Type:** `https://api.publiq.be/probs/url/path-parameter-invalid`
*   **Title**: `Path parameter invalid`
*   **Status**: `404`

The value of a given path parameter (variable parts of a URL) is invalid. More info on what parameter specifically can be found in the `detail` property of the response.

<!-- theme: warning -->

> **Note to API designers**
>
> This error implies that part of the URL path actually contains data that has to be validated, which breaks the concept that the URL is just an identifier for a resource that is either found or not.
>
> Usage of URL paths that contain data that has to validated is discouraged in new APIs or new API endpoints. Instead the data should be passed as query parameters or as JSON in the request body.
>
> This error type should thus only be used on historical endpoints that still expect data as part of the URL path.
