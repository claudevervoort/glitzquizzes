# What's next in LTI

## Question

![Not a cookie!](/lti/assets/quiz_not_cookie.png)

The cookie replacement is based on:

- [ ] An IFrame can access state as long as it is in the same domain or subdomain
- [X] Cross-site communication through Windows PostMessage
- [ ] Semi-permanent storage: The LMS must use local storage to store state
- [X] Transient storge: State may be cleared when user's navigate to another LMS page

The state is by strict domain matching only. LMS may store the state simply in memory since it is not required to survive navigation.

## Question

![Context Groups](/lti/assets/quiz-groups.png)

Which of the following are part of Context Groups specification?

- [X] Group Sets (groups of group)
- [ ] Group roles (member, admin) 
- [X] Group membership substitution parameter
- [ ] Group management (add/remove members)
- [X] Extension to Names and Roles to include Group membership

Context group is a simple service to get a list of groups and their members.

## Question

No more Copy/Paste! No more configuration errors! Dynamic Registration enables:

- [X] Fully automatic registration of OAuth/OpendId and LTI including services and messages/placements
- [ ] Fully automatic registration of Oauth/OpendId Only
- [ ] Semi-automatic OAuth/LTI registration. Still needs to copy/paste the generated client id and token end point.

Yep it does it all!

## Question

![Submission Review](/lti/assets/quiz-subreview.png)

Submission Review is a new UI flow (LTI Message) that allows:

- [ ] To pass submission data for analysis to a tool analyzer
- [X] To launch from the student's score in the LMS directly in the student's work in the tool.

Yes, on click to see the student work. No more awkward navigation,


## Question

![Submission Review](/lti/assets/quiz-subreview.png)

Which submission review, you can also update or set the student's grade.

- [X] Yes, you can modify the grade
- [ ] No, submission review is only to see the student's work 

Right, the submission review launch always contains the line item URL needed to post grade back.

## Question

![Proctoring](/lti/assets/quiz-proctor.png)

How would you qualify the current proposal for the LTI Proctoring spec?

- [ ] Allows you to use any proctoring solution to configure and proctor any activity served from your LMS
- [X] Allows Assessment platform to run a pre-flight launch to set the proctoring session

In this iteration, the specification focuses on native assessment delivery, and does not cover configuration. Start a proctoring session, take the assessment, close the session.

## Question

![Quiz](/lti/assets/quiz-quiz.png)

The LTI Activity specifcation re-uses and profiles many LTI specifications to allow to embed LTI not as standalone activities, but as an activity item part of wider activity.  Like a question in a Quiz. Which specifcations does it re-use/extend?


- [ ] Course Groups
- [X] Deeep Linking
- [X] Submission Review
- [X] Assignnment and Grade Services
- [ ] Names and Roles Services

It also adds an new item type in Deep Linking and introduces the concept of submissions (and multiple submissions).


