# HTTP response status codes
	HTTP response status codes indicate whether a specific HTTP request has been successfully completed.
	Responses are grouped in five classes:
		1.Informational responses (100–199)
		2.Successful responses (200–299)
		3.Redirection messages (300–399)
		4.Client error responses (400–499)
		5.Server error responses (500–599)
## Information responses
	1. 100(Continue)
		This interim response indicates that the client should continue the request or ignore
		the response if the request is already finished.
		
	2. 102 Processing (WebDAV)
		This code indicates that the server has received and is processing the request,
		but no response is available yet.
		
## Successful responses
	1. 200 OK
		The request succeeded. The result meaning of "success" depends on the HTTP method:
			GET: The resource has been fetched and transmitted in the message body.
			HEAD: The representation headers are included in the response without any message body.
			PUT or POST: The resource describing the result of the action is transmitted in the message body.
			TRACE: The message body contains the request message as received by the server.
			
	2. 201 Created
		The request succeeded, and a new resource was created as a result. This is typically the response
		sent after POST requests, or some PUT requests.
		
	3. 202 Accepted
		The request has been received but not yet acted upon. It is noncommittal, since there is no way in
		HTTP to later send an asynchronous response indicating the outcome of the request. It is intended 
		for cases where another process or server handles the request, or for batch processing.
		
	4. 204 No Content
		There is no content to send for this request, but the headers may be useful. The user agent may update
		its cached headers for this resource with the new ones
		
	5. 205 Reset Content
		Tells the user agent to reset the document which sent this request
		
	6. 206 Partial Content
		This response code is used when the Range header is sent from the client to request only part of a resource.
		
## Client error responses
	1. 400 Bad Request
		The server could not understand the request due to invalid syntax.
		
	2. 401 Unauthorized
		Although the HTTP standard specifies "unauthorized", semantically this response means "unauthenticated".
		That is, the client must authenticate itself to get the requested response.
		
	3. 402 Payment Required 
		This response code is reserved for future use. The initial aim for creating this code was using it for digital
		payment systems, however this status code is used very rarely and no standard convention exists.

	4. 403 Forbidden
		The client does not have access rights to the content; that is, it is unauthorized, so the server is refusing to
		give the requested resource. Unlike 401 Unauthorized, the client's identity is known to the server.

	5. 404 Not Found
		The server can not find the requested resource. In the browser, this means the URL is not recognized. In an API,
		this can also mean that the endpoint is valid but the resource itself does not exist. Servers may also send this response
		instead of 403 Forbidden to hide the existence of a resource from an unauthorized client. This response code is probably
		the most well known due to its frequent occurrence on the web.

	6. 405 Method Not Allowed
		The request method is known by the server but is not supported by the target resource. For example, an API may not allow
		calling DELETE to remove a resource.

	7. 406 Not Acceptable
		This response is sent when the web server, after performing server-driven content negotiation, doesn't find any content
		that conforms to the criteria given by the user agent.

	8. 407 Proxy Authentication Required
		This is similar to 401 Unauthorized but authentication is needed to be done by a proxy.

	9. 408 Request Timeout
		This response is sent on an idle connection by some servers, even without any previous request by the client.
		It means that the server would like to shut down this unused connection. This response is used much more since some browsers,
		like Chrome, Firefox 27+, or IE9, use HTTP pre-connection mechanisms to speed up surfing. Also note that some servers merely
		shut down the connection without sending this message.
		
## Server error responses
	1. 500 Internal Server Error
		The server has encountered a situation it does not know how to handle.
		
	2. 501 Not Implemented
		The request method is not supported by the server and cannot be handled. The only methods that servers are required to 
		support (and therefore that must not return this code) are GET and HEAD.
	3. 502 Bad Gateway
		This error response means that the server, while working as a gateway to get a response needed to handle the request,
		got an invalid response