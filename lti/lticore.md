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

Ok, yuo've given your information. Yoou've been registered in the Learning Platform. What is the information you need back from the platform to complete the registration on your side?

- [ ]


## Question

![Super Launch?](/lti/assets/ltilaunchqm_sm.png)

In LTI, all starts with the LTI Launch. A Super Launch! Super enough to make the jump to an external tool transparent to the student, as if it was an extension of their online course.

To achieve this, what is the data usually included in the launch?

- [X] User identity (at least a user identifier)
- [X] The Course (Context) identifier
- [ ] The Student personal needs info
- [X] The role of that user in that Course (Context)
- [X] The identifier of the resource to be launched

The LTI launch contains also other data such as information about the learning platform, the LTI services endpoints, ...

## Question

Ok, let's go technical now. What is the protocol the LTI Launch is based on (hint: the LTI Launch contains the launching user identity's information)?

- [ ] Ad-hoc LTI protocol based on a signed redirection URL
- [X] OpenID
- [ ] SAML
- [ ] Just sending a JSON Web Token (using the Open Id claims definition) to the tool's resource URL (launch URL)

In LTI, the Learning Platform is acting as the Identity Provider.

