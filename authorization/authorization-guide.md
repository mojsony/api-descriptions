<span class="icon"></span>Authorization API Guide
======================
Authorization API enables authorization of sensitive actions performed by customers or agents using 2nd factor authentication. Sensitive action authorizations can be explicitly requested by applications or they can be initiated by APIs during authorization checking. Support for 4 eyes verification and separation of duties will be added in future.

Key Resources
-------------
Authorization API has one top level resource `otp` with three subresources `sms`, `email` and `oath`: 

Resource | Description
----------- |-----------
*otp* | Provides operations related to one-time passwords
*otp/sms* | Provides operations specific to SMS one-time passwords
*otp/email* | Provides operations specific to email one-time passwords
*otp/oath* | Provides operations specific to OATH one-time passwords such TOTP and HOTP

Getting started tutorial
---------------
To get started follow these steps:

###1. Authenticate your app
Action Authorization API uses OAuth 2.0 for authentication. You get an access token that authenticates your app with a particular set of permissions for a user. You provide an access token through an HTTP header:
```
Authorization: bearer {token}
```
To obtain an access token and sign the user in, see [authentication](common-getstarted.html#authentication) section.

###2. URL Root
Now that you've authenticated your app, you can call the Content Management API with your access token against the URL root below, combined with one of the root resources.  Content Management API URLs are relative to the following root unless otherwise noted.

API | URL Root
--------|---------
Authorization API | `https://dev.asseco-see.com/v1/authorization`

> **Note**: Throughout this documentation, only partial syntax such as: 
`GET /otp/sms` is used for the sake of brevity. 
Prefix the path with the correct root URL in order to obtain the full resource path or URL.

###3. Send SMS OTP to unregistered user
To send SMS one-time password to new user who has not been registered you can use phone number.

```http
POST /otp/sms/send HTTP/1.1
Content-Type: application/json

{
  "action": "registration",
  "phone-number": "381654263874"
}
```
You will get back `202 Accepted` status code and json representation of verification id that has been initiated.

```http
HTTP/1.1 202 Accepted
Content-Type: application/json

"6ud2Us85s9"
```
> You need to keep `verification-id` to use it later to verify OTP that was sent via SMS.

###4. Send SMS OTP to registered user
Once user has been registered in the system and his primary mobile number is known, you can use `user-id` to send SMS OTP. You can also provide optional message to be include in SMS.

```http
POST /otp/sms/send HTTP/1.1
Content-Type: application/json

{
  "action": "cross-border-transfer",
  "user-id": "nodjo-001",
  "message": "Please verify your cross border transfer with following code:"
}
```
You will get back `202 Accepted` status code and json representation of verification id that has been initated.

```http
HTTP/1.1 202 Accepted
Content-Type: application/json

"6ud2Us85s9"
```

###5. Verify SMS OTP
Once user has entered code received via SMS, you can verify it by supplying `verification-id` along with the code user entered

```http
POST /otp/sms/verify HTTP/1.1
Content-Type: application/json

{
  "verification-id": "6ud2Us85s9",
  "otp": "782121"
}
```
You will get back `204 No content` status code that confirms that SMS OTP is valid.

```http
HTTP/1.1 204 No content
```

###5. Verify TOTP or HOTP
Users having soft or hardware based tokens can use them to generate OTP that can be used to verify sensitive actions. To verify time or counter based OTP you need to supply `user-id` with OTP that user entered in your application. 

```http
POST /otp/oath/verify HTTP/1.1
Content-Type: application/json

{
  "user-id": "nodjo-001",
  "otp": "928164"
}
```
You will get back `204 No content` status code that confirms that supplied OTP is valid.

```http
HTTP/1.1 204 No content
```

**Congratulations!** You have completed getting started tutorial on most common steps when working with Authorization API. To learn more look at the reference documentation for [available operations](authorization.html).