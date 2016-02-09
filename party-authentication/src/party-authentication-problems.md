   
Possible problems
=================

When request is valid and no standard status code describes situation, Party Authentication API will return status code `440` with one of the following problems in the payload. To learn more see general guidance on [error handling]()

Literal                                |  Code| Description                                                                                                                          
---------------------------------------|-----:|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
invalid_request						   | 53201| The request is missing a required parameter, includes an invalid parameter value, includes a parameter more than once, or is otherwise malformed.
unauthorized_client   				   | 53202| The client is not authorized to request an authorization code using this method.
access_denied						   | 53203| The resource owner or authorization server denied the request.
unsupported_response_type              | 53204| The authorization server does not support obtaining an authorization code using this method.
invalid_scope                          | 53205| The requested scope is invalid, unknown, or malformed.
server_error                           | 53206| The authorization server encountered an unexpected condition that prevented it from fulfilling the request.
temporarily_unavailable                | 53207| The authorization server is currently unable to handle the request due to a temporary overloading or maintenance of the server. HTTP redirect.)
interaction_required                   | 53208| The Authorization Server requires End-User interaction of some form to proceed. This error MAY be returned when the prompt parameter value in the Authentication Request is none, but the Authentication Request cannot be completed.
login_required                         | 53209| The Authorization Server requires End-User authentication. This error MAY be returned when the prompt parameter value in the Authentication Request is none, but the Authentication Request cannot be completed 
account_selection_required             | 53210| The End-User is REQUIRED to select a session at the Authorization Server. The End-User MAY be authenticated at the Authorization Server with different associated accounts, but the End-User did not select a session. 
consent_required                       | 53211| The Authorization Server requires End-User consent. This error MAY be returned when the prompt parameter value in the Authentication Request is none, but the Authentication Request cannot be completed.
invalid_request_uri                    | 53212| The request_uri in the Authorization Request returns an error or contains invalid data.
invalid_request_object                 | 53213| The request parameter contains an invalid Request Object.
request_not_supported                  | 53214| The OP does not support use of the request parameter
request_uri_not_supported              | 53215| The OP does not support use of the request_uri parameter
registration_not_supported             | 53216| The OP does not support use of the registration parameter
