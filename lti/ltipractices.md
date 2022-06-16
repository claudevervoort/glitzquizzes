# LTI Good Practice? Bad Practice?

## Question

When a launch occurs and the lms user id is new to the tool, the tool should NEVER prompt the user for login.

- [ ] Good practice
- [ ] Bad practice
- [X] It depends

Whether or not the user needs to create an account on the tool really depends on the tool. But, if prompting, this should only happen on the 1st launch. Asking on every launch would really be... bad practice!

## Question

A tool should rely on email passed by the LMS to identify the user, and even possibly automatically bind account if a tool's user have the same email.

- [ ] Good practice
- [X] Bad practice

## Question

You should avoid storing the user's email or names for an extended period of time.

- [X] Good practice
- [ ] Bad practice

If your tool can avoid storing Personally Identifiable Data and rather rely on the launch data, then that's one less thing to worry about...

## Question

A tool should use deep linking picker flow to import LTI Links in a course.

- [X] Good practice
- [ ] Bad practice

Let's keep the plumbing hidden. nNo more copy/paste, no more link settings to fill, or over reliance on resource_link_id.

## Question

If the link is to a graded activity, you should include a line item in the resource link definition included in the deep linking response.

- [X] Good practice
- [ ] Bad practice, you should always create line item (gradebook column) using Assignment and Grade Service

It's usually preferred to include the line item so the LMS will create the link and the line item as part of the same operation. In addition the LMS will be aware the line item is related to that given link, allowing in some platforms additional features in the gradebook.

## Question

When launching a resource link as an instructor, the instructor should be provided with the options to:

- [X] preview the activity
- [X] edit the activity
- [ ] review students' work for all activities in context
- [X] review students' work for that activity only

Of course whether those options are available depends if they also make sense from the tool's logic.

## Question

Tool should stick to a single user's submission per activity.

- [ ] Yes!
- [X] Baloney

A tool is not limited to the number of submissions, it must just properly aggregate the score and post an updated score each time the aggregated score value changes.

## Question

When a student completes the work that requires manual grading, the tool should wait until the instructor has graded the work before to post a score to the learning platform

- [X] Bad practice
- [ ] Good practice

When the student completes the work, a tool should send a completed but waiting manual grade status to the learning platform so that the platform may for example display a needs grading icon in their gradebook.

## Question

When in a tool the instructor resets the student's work so that the student could start over, the tool should:

- [ ] Do nothing, and only send an updated score when the student completes the work again
- [ ] Send a Score with a activity status of initialized and a score of 0
- [X] Send a Score with a activity status of initialized and no score value

It's important to notify the learning platform the activity has been reset, so that can be reflected in the platform's gradebook.

## Question

![Submission Review](/lti/assets/quiz-subreview.png)

Your tool receives a submission review request, it should:

- [X] Show the work for the graded student for the given activity
- [ ] Show the work of all course students for the given activity

Submission Review launches let the instructor directly navigate to a student work.



