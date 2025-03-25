# API Documentation

URL: `https://api.clearsky.services`

status: `https://status.clearsky.app`

## Response Errors
- **400:** Bad Request
- **404:** Not Found
- **409:** Conflict
- **413** Payload Too Large
- **423:** Locked
- **429:** Too Many Requests
- **500:** Internal Server Error
- **501:** Not Implemented
- **503:** Service Unavailable

## Rate Limiting

Anonymous endpoints:
- **Limits:** 5 requests per second

Authenticated endpoints:
- **Limits:** 30 requests per second

## Endpoints

### Anonymous:

#### 1.

- **Endpoint:** `/api/v1/anon/get-did/<handle>`
  - **Method:** `GET`
    - **Description:** Get the DID of a given handle
    - **Parameters:** handle
      - **Response:**
          ```json
              {
                  "data": 
                      {
                          "identifier": str,
                          "did_identifier": str,
                      }
              }

#### 2.

- **Endpoint:** `/api/v1/anon/get-handle/<did>`
  - **Method:** `GET`
    - **Description:** Get the handle of a given DID
    - **Parameters:** DID
      - **Response:**
          ```json
              {
                  "data": 
                      {
                          "identifier": str,
                          "handle_identifier": str,
                      }
              }

#### 3.

- **Endpoint:** `/api/v1/anon/total-users`
  - **Method:** `GET`
    - **Description:** Get user count information: total users, active users, deleted users
    - **Parameters:** none
      - **Response:**
          ```json
                {
                    "data": 
                        {
                            "active_count": 
                                {
                                    "value": int,
                                    "displayName": str
                                },
                            "total_count": 
                                {
                                    "value": int,
                                    "displayName": str
                                },
                            "deleted_count": 
                                {
                                    "value": int,
                                    "displayName": str
                                },
                        }, 
                    "as of": timestamp
                }

#### 4.

- **Endpoint:** `/api/v1/anon/validation/validate-handle/<handle>`
  - **Method:** `GET`
    - **Description:** Validate a handle
    - **Parameters:** handle
      - **Response:**
          ```json
              {
                  "data": 
                      {
                          "valid": bool
                      }, 
                  "identity": str
              }
  
### 5.

- **Endpoint:** `/api/v1/anon/uri-url/<uri>`
  - **Method:** `GET`
    - **Description:** Get the URL of a given URI
    - **Parameters:** URI
      - **Response:**
          ```json
              {
                  "data": 
                      {
                          "url": str
                      }
              }

### 6.

- **Endpoint:** `/api/v1/anon/lists/fun-facts`
  - **Method:** `GET`
    - **Description:** Get top 20 blockers and blocked
      - **Parameters:** None
        - **Response:**
            ```json
                {
                    "data": 
                        {
                            "blocked": 
                                [
                                    {
                                        "did": str,
                                        "count": int,
                                    }
                                ],
                            "blockers": 
                                [
                                    {
                                        "did": str,
                                        "count": int,
                                    }
                                ],
                        }, 
                    "as of": timestamp
                }
      
### 7.

- **Endpoint:** `/api/v1/anon/lists/funer-facts`
  - **Method:** `GET`
    - **Description:** Get top 20 blockers and blocked in the last 24 hours
    - **Parameters:** None
    - **Response:**
        ```json
            {
                "data": 
                    {
                        "blocked": 
                            [
                                {
                                    "did": str,
                                    "count": int,
                                }
                            ],
                        "blockers": 
                            [
                                {
                                    "did": str,
                                    "count": int,
                                }
                            ],
                    }, 
                "as of": timestamp
            }

### 8.

- **Endpoint:** `/api/v1/anon/lists/block-stats`
  - **Method:** `GET`
    - **Description:** Get a list of block stats based on userbase
      - **Parameters:** None
        - **Response:**
            ```json
                {
                    "data": 
                        {
                            "numberOfTotalBlocks": int,
                            "numberOfUniqueUsersBlocked": int,
                            "numberOfUniqueUsersBlocking": int,
                            "totalUsers": int,
                            "percentUsersBlocked": int,
                            "percentUsersBlocking": int,
                            "numberBlock1": int,
                            "numberBlocking2and100": int,
                            "numberBlocking101and1000": int,
                            "numberBlockingGreaterThan1000": int,
                            "percentNumberBlocking1": int,
                            "percentNumberBlocking2and100": int,
                            "percentNumberBlocking101and1000": int,
                            "percentNumberBlockingGreaterThan1000": int,
                            "averageNumberOfBlocks": int,
                            "numberBlocked1": int,
                            "numberBlocked2and100": int,
                            "numberBlocked101and1000": int,
                            "numberBlockedGreaterThan1000": int,
                            "percentNumberBlocked1": int,
                            "percentNumberBlocked2and100": int,
                            "percentNumberBlocked101and1000": int,
                            "percentNumberBlockedGreaterThan1000": int,
                            "averageNumberOfBlocked": int
                        }, 
                    "as of": timestamp
                }

### 9.

- **Endpoint:** `/api/v1/anon/get-list/<handle/did>` `/api/v1/anon/get-list/<handle/did>/<page:int>`
  - **Method:** `GET`
    - **Description:** Get list of moderation lists a user is on
      - **Parameters:** handle or did
        - **Response:**
            ```json
                {
                    "data": 
                        {
                            "identifier": str, 
                            "lists": 
                                [
                                    {
                                        "url": str,
                                        "did": str,
                                        "name": str,
                                        "description": str,
                                        "created_date": timestamp,
                                        "date_added": timestamp,
                                    }
                                ]
                        }
                }

### 10.

- **Endpoint:** `/api/v1/anon/get-list/total/<handle/did>`
  - **Method:** `GET`
    - **Description:** Get the total number of moderation lists a user is on
      - **Parameters:** handle or did
        - **Response:**
            ```json
                  {
                      "identity": str, 
                      "status": bool, 
                      "data": 
                          {
                              "count": int
                          }
                  }
          
### 11.

- **Endpoint:** `/api/v1/anon/blocklist/<handle/did>` `/api/v1/anon/blocklist/<handle/did>/<page:int>`
  - **Method:** `GET`
    - **Description:** Get list of lists that a user is blocking
      - **Parameters:** handle or did
        - **Response:**
            ```json
                  {
                      "identity": str, 
                      "status": bool, 
                      "data": 
                          {
                              "blocklist": 
                                  [
                                      {
                                          "did": str,
                                          "blocked_date": timestamp
                                      }
                                  ],
                          }
                  }

### 12.

- **Endpoint:** `/api/v1/anon/single-blocklist/<handle/did>` `/api/v1/anon/single-blocklist/<handle/did>/<page:int>`
  - **Method:** `GET`
    - **Description:** Get list of lists that a user is blocked on
      - **Parameters:** handle or did
        - **Response:**
            ```json
                  {
                      "identity": str, 
                      "status": bool, 
                      "data": 
                          {
                              "blocklist": 
                                  [
                                      {
                                          "did": str,
                                          "blocked_date": timestamp
                                      }
                                  ],
                          }
                  }
          
### 13.

- **Endpoint:** `/api/v1/anon/blocklist/total/<handle/did>`
  - **Method:** `GET`
    - **Description:** Get the total number of lists a user is blocking
      - **Parameters:** handle or did
        - **Response:**
            ```json
                  {
                      "identity": str, 
                      "status": bool, 
                      "data": 
                          {
                              "count": int
                          }
                  }
          
### 14.

- **Endpoint:** `/api/v1/anon/single-blocklist/total/<handle/did>`
  - **Method:** `GET`
    - **Description:** Get the total number of lists a user is blocked on
      - **Parameters:** handle or did
        - **Response:**
            ```json
                  {
                      "identity": str, 
                      "status": bool, 
                      "data": 
                          {
                              "count": int
                          }
                  }
          
### 15.

- **Endpoint:** `/api/v1/anon/get-profile/<handle/did>`
  - **Method:** `GET`
    - **Description:** Get Profile information of a user
      - **Parameters:** handle or did
        - **Response:**
            ```json
                  {
                      "data": 
                          {
                              "identifier": str,
                              "handle": str,
                              "did_identifier": str,
                              "user_url": str,
                              "pds": str,
                              "created_date": timestamp,
                              "placement": int,
                          }
                  }
      
### 16.

- **Endpoint:** `/api/v1/anon/subscribe-blocks-blocklist/<handle/did>` `/api/v1/anon/subscribe-blocks-blocklist/<handle/did>/<page:int>`
  - **Method:** `GET`
    - **Description:** Get list of lists that a user is blocking
      - **Parameters:** handle or did
        - **Response:**
            ```json
                {
                    "identity": str, 
                    "status": bool, 
                    "data": 
                        {
                            "blocklists": 
                                [
                                    {
                                        "list_uri": str,
                                        "date_added": timestamp,
                                        "list_owner": str,
                                        "list_url": str,
                                        "list_name": str
                                    }
                                ],
                        }
                }
                
### 17.

- **Endpoint:** `/api/v1/anon/subscribe-blocks-single-blocklist/<handle/did>` `/api/v1/anon/subscribe-blocks-single-blocklist/<handle/did>/<page:int>`
  - **Method:** `GET`
    - **Description:** Get list of lists that a user is blocked on
      - **Parameters:** handle or did
        - **Response:**
            ```json
                {
                    "identity": str, 
                    "status": bool, 
                    "data": 
                        {
                            "blocklists": 
                                [
                                    {
                                        "list_uri": str,
                                        "date_added": timestamp,
                                        "list_owner": str,
                                        "list_url": str,
                                        "list_name": str
                                    }
                                ],
                        }
                }

### 18.

- **Endpoint:** `/api/v1/anon/lists/dids-per-pds`
  - **Method:** `GET`
    - **Description:** Return a list of the count of users on each PDS
      - **Parameters:** None
        - **Response:**
            ```json
                {
                    "data": 
                        [
                            {
                                "pds": str,
                                "did_count": timestamp
                            }
                        ]
                }

### 19.

- **Endpoint:** `/api/v1/anon/search/moderation-lists/<name:string>` `/api/v1/anon/search/moderation-lists/<name:string>/<page:int>`
  - **Method:** `GET`
    - **Description:** Get a list of lists and other details based on word search of either the list name or description
    - **Parameters:** name
      - **Response:**
          ```json
              {
                  "input": str, 
                  "data": 
                      {
                          "lists": 
                              [
                                  {
                                      "url": str,
                                      "did": str,
                                      "name": str,
                                      "description": str,
                                      "created_date": timestamp,
                                  }
                              ], 
                          "pages": int
                      }
              }
      
### 20.

- **Endpoint:** `/api/v1/anon/get-handle-history/<handle/did>`
  - **Method:** `GET`
    - **Description:** Get the account history of a user
    - **Parameters:** handle or did
      - **Response:**
          ```json
              {
                  "data": 
                      {
                          "identifier": identifier,
                          "handle_history": [[str, str, str]]
                      }
              }

### 21.

- **Endpoint:** `/api/v1/anon/images/logo`
  - **Method:** `GET`
    - **Description:** Get the logo image
    - **Parameters:** None
    - **Response:** png3

### 22.

- **Endpoint:** `/api/v1/anon/status/time-behind`
  - **Method:** `GET`
    - **Description:** Get the time behind status of clearsky data
    - **Parameters:** None
      - **Response:**
        ```json
            {
                "data": 
                    {
                        "time behind": str
                    }
            }
        
### Authenticated:

For information about authenticated endpoints please contact us at [support@clearsky.app](mailto:support@clearsky.app)