# Do you know your LTI

## Question

*Home Sweet Home* Who is charge of the LTI specifications?**

- [ ] IETF
- [x] IMS Global (1EdTech)
- [ ] W3C
- [ ] ADL

IMS Global (aka 1EdTech) is also the stewards of many other ed-tech specifications.

## Question

Do you know your LTI? LTI stands for:

- [X] Learning Tools Interoperability
- [ ] Learning Technology Interface
- [ ] LMS Tool Interface

And it's all in the name! LTI defines a standards way for Learning Tool to integrate and extend the native capabilities of Learning Platforms (like ypur favorite Learning Management System). Like a cool simulation, fancy ebooks, outworldly quizzes, or captivating interactive content. Same integration across learning platforms. That's the promise...

## Question

Talking about **seamless** integration, what is the key goal of LTI?

- [X] To extend an online course with external activities
- [ ] To allow a tool to integrate with the back-end services from the school/institution
- [ ] To offer a tool a single-sign on mechanism with the school/institution infrastructure
- [ ] The CSV batch export of courses, users and members
- [ ] Single-Sign on mechanism

Yes, LTI is first and foremost a UI integration on additional resources in a learning platform.

## Question

But how is this integration achieved?

- [ ] A batch/CSV API to exchange course, roster and assignment
- [X] A special browser launch to the tool
- [ ] A REST API that exposes the learning platform's data to the tool

![Super Launch](/lti/assets/ltilaunch_sm.png)

Yes, it all starts with the launch, where the course member clicks on that special link in the course site that opens up the tool. It's a super launch...

## Question

![Super Launch?](/lti/assets/ltilaunchqm_sm.png)

Super Launch? This means the launch is enriched with contextual data allowing the user to bootstrap the tool's experience. What is the data usually included in the launch?

- [X] User identity (at least a user identifier)
- [X] The Course (Context) identifier
- [ ] The Student personal needs info
- [X] The role of that user in that Course (Context)
- [X] The identifier of the resource to be launched

The LTI launch contains also other data such as information about the learning platform, the LTI services endpoints, ...

## Question

Ok it's nice to pass all that data, but it needs to be trusted by the tool to be usable. A key element of the LTI specification is thus to establish the trust between a learning platform and a tool. In LTI 1.3, how is the trust achieved?

- [ ] a key and a secret are shared between both parties
- [X] each party shares their public keys, no secret is exchanged!

Yes, and that is a key differentiator with the previous version of LTI. No secret is shared, less chance for breaches!

## Question

Talking about version, what is the latest version of
the LTI Core specification?

- [ ] LTI 1.0
- [ ] LTI 1.1
- [x] LTI 1.3
- [ ] LTI 2.0
- [ ] LTI Advantage

![Lucky 1.3](/lti/assets/lucky13_sm.png)

Indeed, sometimes you need to go back to go forward! LTI 2 is deprecated, you can forget you knew about it if you did!

## Question

Without going into technical details (there are other glitzquizzes for that!), the technical foundations of the LTI specifcations are:

- [ ] OAuth 1,0a
- [X] OAuth 2 and OpenId
- [ ] JSON Web Token and LTI specific protocol
- [ ] SAML/GraphQL

LTI is a profile of OAuth 2 and OpenId. In particular, it extends the OpenId ID Token claim sets to contain the LTI context data mentionned earlier.

## Question

**What's in the bag?** So LTI Advantage is not a version, it's a bundle of LTI Specifications. What's in that bundle?

- [X] LTI 1.3 Core
- [ ] Course Groups Service
- [X] Deep Linking Service (the picker flow)
- [X] Assignment and Grades Services (the Gradebook API)
- [ ] Dynamic Registration

LTI Advantage bundle definition will probably evolve over time to include additional LTI services. In the meantime, other LTI Specifications are made available. A platform for example may say i'm LTI Advatnage and I also support Dynamic Registration and Course Groups specifications.

## Question

When a vendor claims to be LTI Advantage, does it mean it supports some or all the services?

- [X] all the services if the vendor is a learning platform
- [ ] some of the services for a learning platform vendor
- [ ] all the services for a learning tool vendor
- [X] only the services used for a learning  vendor

An LTI Advantage certified platform guarantees to tools support for a baseline of LTI services. As a tool, the contract is to use only the services that make sense. For example, a tool would not be LTI Advantage if it forces its users to do manual LTI Links creations rather than supporting the picker flow (DeepLinking flow).

## Question

Now let's have a quick review of what those services are. Let's start with Deep Linking Service. What is it for?

- [ ] Offer a REST API to inject LTI links in a course
- [X] A UI Flow to open the tool in a picker mode to select/create links and import them back in the course
- [ ] A special kind of link that opens resources like a chapter inside an ebook (a deep link)

Yeah the name may be a bit tricky, Deep Linking is about... importing LTI Links to resources inside the tool (deep links).

## Question

![Deep Linking Flow](/lti/assets/ltilaunchdl_sm.png)

Deep Linking flow can be used to import in the course:

- [X] LTI Links
- [ ] LTI Tool configurations
- [X] HTML Fragments (embed)
- [X] Images
- [X] Additional types defined by other LTI specifications
- [X] Additional types defined by the Learning Platform

While deep linking is often centered around the import of LTI Links, it may be used to import other kind of assets. What can be imported is advertised by the tool when launching in the tool: *you can give me back lti links and images only* for example. A platform can also say if multiple items may be imported at once.

## Question

Usually the next important need for a tool after being launched from a learning platform is to be able to return a score. This is the role of the Assignment and Score Services API. AGS allows a tool to:

- [ ] post a score to any gradebook column/activity
- [ ] post a score to only the activity that was launched by the student
- [X] post a score to any activity linked to the tool's lti deployment

Right! A key element of LTI Services is to be **sandboxed** to the tool's resources: a tool may access and update its resources in the learning platform, so for example send a score to any of its activities. But it may not post or even see any of the other grade columns or actvitities in the learning platform's course.