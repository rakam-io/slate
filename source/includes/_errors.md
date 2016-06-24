# Errors

Rakam API uses the following error codes:

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is not valid. Please check the parameters for the endpoint and be sure that you use JSON format.
403 | Forbidden -- The API Key is missing or invalid. Please use appropriate api key for the endpoint. Available api keys are write_key, read_key and master_key.
404 | Not Found -- The resource could not found.
405 | Method Not Allowed -- The endpoint does not exist.
429 | Too Many Requests, slow down.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.