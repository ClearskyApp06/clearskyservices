# Clearsky Services

This Application provides raw and aggregated information from Bluesky using ATProto.

## Announcements
Ongoing:
- We are working to finalize v1 of the API, you may see changes as we update responses.
- Some endpoints listed in this documentation may be disabled.

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


## Table of contents

- [Usage](api.md)

## Usage

See the [API Documentation](api.md) for more information on the available endpoints.
