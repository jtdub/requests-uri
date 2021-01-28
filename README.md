# Ansible Collection - jtdub.requests.uri

Documentation for the collection.

# INSTALL REQUIREMENTS

- [ ] Install `requests`: `pip install requests`

## DOCUMENTATION
```
---
module: jtdub.requests.uri
short_description: Utilizes the python requests library to make HTTP calls to remote resources
description:
    - This module utilizes the python requests library to make HTTP calls to remote resources.
      It attempts to be a full featured implmentation of the requests library for use in Ansible
      playbooks.
author: James Williams (@packetgeeknet)
requirements:
    - requests
    - json
options:
    method:
        description: method for the new Request object
        choices:
        - GET
        - POST
        - OPTIONS
        - HEAD
        - PUT
        - PATCH
        - DELETE
        required: False
        default: GET
    url:
        description: URL for the new Request object
        required: True
    params:
        description: Dictionary, list of tuples or bytes to send in the query string for the Request.
        required: False
        default: null
    data:
        description: Dictionary, list of tuples, bytes, or file-like object to send in the body of the Request.
        required: False
        default: null
    json:
        description: A JSON serializable Python object to send in the body of the Request.
        required: False
        default: null
    headers:
        description: Dictionary of HTTP Headers to send with the Request.
        required: False
        default: null
    cookies:
        description: Dict or CookieJar object to send with the Request.
        required: False
        default: null
    files:
        description:
            - Dictionary of 'name': file-like-objects (or {'name': file-tuple}) for multipart encoding upload.
              file-tuple can be a 2-tuple ('filename', fileobj), 3-tuple ('filename', fileobj, 'content_type')
              or a 4-tuple ('filename', fileobj, 'content_type', custom_headers), where 'content-type' is a string
              defining the content type of the given file and custom_headers a dict-like object containing additional
              headers to add for the file.
        required: False
        default: null
    username:
        description: Username for auth tuple to enable Basic/Digest/Custom HTTP Auth.
        required: False
        default: null
        required_with: password
    password:
        description: Password for auth tuple to enable Basic/Digest/Custom HTTP Auth.
        required: False
        default: null
        required_with: username
        no_log: True
    timeout:
        description:
            - How many seconds to wait for the server to send data before giving up, as a float,
              or a (connect timeout, read timeout) tuple.
        required: False
        default: null
    allow_redirects:
        description: Boolean. Enable/disable GET/OPTIONS/POST/PUT/PATCH/DELETE/HEAD redirection.
        required: False
        default: True
    proxies:
        description: Dictionary mapping protocol to the URL of the proxy.
        required: False
        default: null
    verify:
        description:
            - Either a boolean, in which case it controls whether we verify the server’s TLS certificate,
              or a string, in which case it must be a path to a CA bundle to use.
        required: False
        default: True
    stream:
        description: if False, the response content will be immediately downloaded.
        required: False
        default: True
    cert_key:
        description: Tuple of (‘cert’, ‘key’) pair
        required: False
        default: null
    cert_file:
        description: Srring of path to ssl client cert file (.pem)
        required: False
        default: null
```
## EXAMPLES
```
- jtdub.requests.uri:
    method: GET
    url: https://google.com/
- jtdub.requests.uri:
    method: GET
    url: https://bgpstuff.net/totals?format=json
    headers:
      Content-type: "application/json"
```
## RETURN
```
changed:
    description: Whether the request changed information
    type: boolean
    sample: True
content:
    description: Response value in bytes
    type: bytes
cookies:
    description: Respsonse cookies
    type: dictionary
elapsed:
    description: Elapsed time of request in microseconds
    type: integer
encoding:
    description: Response encoding
    type: string
headers:
    description: Response Headers
    type: dictionary
history:
    description: Request history
    type: list
is_permenant_redirect:
    description: Response with HTTP 301
    type: boolean
is_redirect:
    description: Response with HTTP 30x
    type: boolean
json:
    description: Response with JSON content
    type: dictionary
links:
    description: Response with URL links
    type: dictionary
next:
    description: Response with pagination next page
    type: string
ok:
    description: Request ok?
    type: boolean
reason:
    description: Response reason
    type: string
    sample: ok
status_code:
    description: Request status code
    type: integer
    sample: 200
text:
    description: Response text
    type: string
url:
    description: URL sent in request
    type: string
verify:
    description: Verify secure certificates
    type: boolean
    sample: True
```
