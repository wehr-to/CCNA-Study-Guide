## Oauth 2.0
- Secure authentication framework that is widely used in web apps
- Provides access delegation, granting third party apps limited access to resources on behalf of the resources owner
- no need to share the resource owners credentials with the third party

### Examples of Oauth2.0 
- Logging in with google / Many websites and apps offer the option to log in using your google account

#### Connecting apps to social media accounts 
- Many apps can be connected to accounts on social media platforms like IG, FB, linkedin etc

4 Components: 
- Client app: app requesting access
- Resource owner: Acc owner granting access to their data, ex: Logging in via google
- Auth server: Issues access tokens after user approval, Ex: google oauth service
- Resource server: Hosts the protected resource

6 Steps: 
- 1: Client app requests authorization from the resource owner to access the resource
- 2: Resource owner grants authorization by logging into their account (google account) and giving permission
- 3: The client app exchanges the authorization grant for an access token from the auth server
- 4: the auth server provides an access token to the client app
- 5: The client app sends the access token to the resource server (ex: googles) server hosting calendar data to request the resource
- 6: The resource server validates the access token and provides the requested resource (calendar data) to client app

- The access token granted in step 4 functions just like the token used in bearer authentication
- it grants access to the specified resource within the appropriate scope of access (read only access)
- Access tokens expire after a short period, but Oauth 2.0 uses refresh tokens granted by the auth server to obtain new access tokens without requiring the user to log in every time 
