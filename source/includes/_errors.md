# Errors

The VerticalChange API uses the following error codes:

Error Code | Meaning
---------- | -------
400 | Bad Request -- The request was invalid or cannot be otherwise served.
401 | Unauthorized -- Missing or incorrect authentication credentials.
403 | Forbidden -- The requested resource is not accessible.
404 | Not Found -- The specified resource could not be found.
405 | Method Not Allowed -- You tried to access a resource with an invalid method.
406 | Not Acceptable -- You requested a format that isn't json.
410 | Gone -- The requested resource has been removed from our servers.
429 | Too Many Requests -- You're requesting too many resources.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
