# Clearsky Services API

This Application provides raw and aggregated information from Bluesky using ATProto.

## Announcements
Ongoing:
- We are working to finalize v1 of the API, you may see changes as we update responses.
  - NOTE: Some changes will be announced and others will not.
- Some endpoints listed in this documentation may be disabled.
- Validating error responses.

10/16/2025:

We will be updating error responses very soon. The format will be changing to be more standardized.

example:
```json
{
    "status": 401,
    "error_type": "Unauthorized",
    "message": "Unauthorized: Authentication credentials are missing or invalid."
}
```
```json
{
    "status": 401,
    "error_type": "Unauthorized",
    "message": "Unauthorized: Authentication credentials are missing or invalid.",
    "details": {
        "authenticated": false,
        "identifier": "thieflord.dev",
        "error": "Unauthorized"
    }
}
```
```json
{
    "status": 500,
    "error_type": "InternalServerError",
    "message": "An unexpected error occurred on the server.",
    "details": "Failed to load record"
}
```

10/18/2025:

Error responses have been updated to the new format.

10/20/2025:

We will be updating how pagination functions across the API. The changes will be as follows:
- All endpoints that support pagination will now use a consistent approach with `limit` and `cursor` parameters.
- The `limit` parameter will define the maximum number of items to return. For now, the maximum limit will be the default limit and cannot be increased.
- The `cursor` parameter will be used to fetch the next set of results based on the last item of the previous response.
- The response will include a `cursor` field if there are more results to fetch.
- This change aims to simplify pagination and make it more predictable across all endpoints.
- We will announce when these changes go live.

10/23/2025:
We will be updating how params are sent to the API. The changes will be as follows:
- All endpoints will be converted to use query parameters for GET requests

Example:

Instead of:

```GET /api/v1/anon/blocklist/{identifier}```

We will use:

```GET /api/v1/anon/blocklist?identifier={identifier}```

This change will roll out with the new pagination changes.

## Issues
If you encounter any issues or have suggestions for improvements, please open an issue ticket on our [GitHub repository](https://github.com/ClearskyApp06/clearskyservices/issues).

## Table of contents

- [Usage](api.md)

## Usage

See the [API Documentation](api.md) for more information on the available endpoints.
