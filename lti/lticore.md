# At the Core, the LTI Launch

## Question

A university wants to make your learning tool to its students. The need to register your tool in the Univeristy's learning platform. Which of those are required information the tool must provide?

- [ ] Tool Name
- [X] Tool Domain(s)
- [ ] Tool Global Identifier
- [X] Authentication Response URL(s)
- [X] Login Initiation URL

Typically a platform will also require the Tool's public key set URL as it is needed for using LTI Advantage services such as Deep Linking and Grade pass back. It will also ask some other configurations to enable additional services. But to support core LTI Resource Link launch, this is enough:

- Login Initiation URL
- Authentication Resonse URL(s)

## Question

Ok, you've given your information. Yoou've been registered in the Learning Platform. What is the information you need back from the platform to complete the registration on your side?

- [X] Client ID for the registration
- [ ] The Platform Name
- [X] The platform's Publick Keyset URL
- [X] The platform's domain (the Issuer domain)
- [ ] The gradebook service URL
- [ ] The Roster and Course service URLs

Wiring done! The registration is entered in both the platform's and the tool's databases. Now let's get our 1st launch going!

## Question

The instructor has added a link to your tool in the course, usually by entering a given Resource URL.

A student enters the course, and clicks on the resource. Which tool URL is the user's browser redirected to?

- [ ] The Tool's Resource URL
- [ ] One of the registered Authorization Redirect URL
- [X] The login initiation URL

Yes, any LTI launch always starts by a request to the login initiation URL. It's the platform ringing on the tool's door: 'Hello, someone wants to get in'.

Let's think of a controller, it would look like:

```
#POST
login_init(iss,client_id,lti_deploy_id,login_hint,lti_hint):
    what happens here?
```

## Question

Someone ring at the door, let's ask who that is! To ask, we need to use some information from the initiation login request. Which one?

- [ ] Login Hint
- [X] Issuer (iss)
- [X] Client Id
- [ ] LTI Message Hint
- [X] Login URL

With the issuer and client id is all you need to lookup the registration data and get the calling platform's authentication request. Passing the client_id is however optional, but widely supported. In the rare case it is not, you will have to rely on the login URL.


```
#POST
login_init(iss,client_id,lti_deploy_id,login_hint,lti_hint):
    reg = get_registration(iss, client_id)
    url = add_parameters_to_url(reg.authentication_request_url, reg, login_hint, lti_hint)
    redirect(url)
```

## Question

The tool's now redirect the user's browser back to the platform using the authentication request URL. The request needs to contain quite a few parameters including the `client_id`. How is this request secured?

- [ ] The request is signed
- [X] The authentication response URL matches one the registered URL for the client_id

Yes, still no signature in sight! The security is guaranteed by the fact the response will only be sent to a preregistered URL. If the authentication response URL is not matching a pre-regsistered one, the launch process is interrupted.

Learning platforms usually adhere to a strict URL match. No templates, no additional query parameters. It must be a total match with one of the registered URLs.

## Question

The platform is now ready to tell you who's is ringing. For that, the user's browser is one more time redirected, now back to the tool, to the authentication response URL. Which parameter is included in that request?

- [ ] A JSON Object with the user and LTI Info
- [X] A JSON WebToken (id_token) with the user and LTI Info

Our code needs to support a new endpoint:

```
#POST
login_init(iss,client_id,lti_deploy_id,login_hint,lti_hint):
    reg = get_registration(iss, client_id)
    url = add_parameters_to_url(reg.authentication_request_url, reg, login_hint, lti_hint)
    redirect(url)

#POST
authenticate(id_token):
    ...
```

The ID Token is a JSON Web Token which contains identity claims. LTI extends it with its additional claims pertaining to the launch.

## Question

The id_token is a signed JWT. How we do we verify the signature?

- [X] Using the Platform's Keyset URL and the JWT Key Id (kid)
- [ ] Using a shared secret
- [ ] Using a provider public key

A tool uses one of the platform's public keys to validate the signature. A platform exposes its public keys through a URL which is communicated at the time of registration. The id_token header contains the `kid` claim which identifies which of the exposed keys was used to sign the JWT.

```
#POST
login_init(iss,client_id,lti_deploy_id,login_hint,lti_hint):
    reg = get_registration(iss, client_id)
    url = add_parameters_to_url(reg.authentication_request_url, reg, login_hint, lti_hint)
    redirect(url)

#POST
authenticate(id_token):
    (iss, clientid) = extract_from_token(id_token)
    registration = load_registration(iss, clientid)
    keyset = fetch_keyset(registration.keyset_url)
    if validate_token(id_token, keyset):
        return proceed_with_launch(id_token)
    else:
        return 401-unauthorized
```
