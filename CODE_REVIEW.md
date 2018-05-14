# Code reviews and PR process

We use PR reviews to achieve the following purposes:
  1. Quality: Increase the quality of the software and, as a consequence, of our product
  2. Training/Coaching/Mentoring: we improve reviewed and reviewers knowledge and skills
  3. Knowledge sharing: we align the team about technical backgrounds and information
  4. Idea gatering: we discuss, share and evaluate ideas that creates opportunities

As a developer you are responsible for the quality of your PR and for the amount of time the PR stays open.
Your PR needs to pass all the reviews steps as fast as possible, you have to communicate and urge the reviewers everytime the PR needs to be reviewed.
You are invited to read carefully your PR before request a review, this can drastically reduce the time your PR stays open before being approved.
Reading multiple times your PR changes in diff tools like github can help you spot parts that can be improved.

## PR steps
### Open a PR

Be sure you are providing the necessary information to speed-up the PR process an to help reviewers doing their part:

* Title should contain the reference to the story/ticket if existing
* Title should summarise the purpose of the implementation by the code POV, not replicate the title of the story that represent usually the user POV
* Description
  1. Should contain link to useful references or resources if available (Jira ticket or tickets, libraries, external documentation...)
  2. You should provide the right context and background information to help reviewers undestand your implemntation choices, avoided un-necessary subsequent questions ('I used xxx because of xyz...')
  3. Tests plan: You should provide a basic tests plan. This is to communicate to reviewers that you knew how the feature is expected to work and can also help human QA.

### Review the code yourself

Before assigning the PR to reviewers it is good practice to review your own code.
This can save time to you and to the reviewers too, avoiding useless back and forth for something that you could have spotted reading your code in github.
Consider the following:

1. Are there ways to simplify the implemented solution while still meeting the defined requirements?
2. Are best practices being applied?
3. Ensure code is well commented and variable naming is easy to understand. 
4. Ask clarifying questions on design decisions to better understand the engineers approach.
5. Check team standards such as logging, environment variables, library usage, and unit testing.

### Assign reviewers

To enforce share knowledge and ideas about the project and the codebase a 2 reviewers process is encoureaged when possible, but not mandatory for small teams. 
When this is applicable, your PR will need to be **'peer approved'** and **'core approved'**.
A peer reviewer is a developer with (very approssimatively) a similar amount of skills and the same seniority and knowledge of the product.
A core reviewer is a developer with more Seniority and a bigger knowledge of the product and of the 'big picture', usually with also wider background of the business requirements.

Once you are ready, you should assign a **peer reviewer** and contact him/her directly or mentioning in the appropriate PR channel.
If he/she is busy he/she can ask you to find some else available. 
On the meantime you should also label the PR **'Waiting for review'**.
To assign reviewers use the relative github feature.

### Incorporating Feedback

Respond to all PR comments on the original PR and commit updates to the original PR.
Open a new PR should always be avoided cause it removes the historical discussion/comments.
Use a new commit for all updates, don’t rebase or force changes and this can cause issues for those reviewing your PR and reduces visibility in the review process.
Feel free to push back on suggestions with clarification of your reasoning.
Ensure the suggested changes don’t move out of scope of the original ticket. Flag any potential future stories or refactoring tasks to the PO and Scrum Master.

### Get the approval

When your **peer reviewer** is happy, he/she have to put the label **'Peer approved'** and you can ask a core reviewer to proceed with his/her review.

When the **core reviewer** is happy, he/she have to put the label **'Ready for QA'** and assign the PR to one or more QA.
The **core reviewer** have to communicate in the your project channel that the story is RFQA (Ready for QA). This can easily done on Slack with the 'jirio' command like: ```/jirio transit WP-1234 Ready for QA```.

This will automatically update the ticket in JIRA accordingly, anyway you are responsible to keep your tickets in the Kanban board always up-to-date.

A **core review** is inclusive of a **peer review**. This mean that if a **core reviewer**'s PR is approved by another **core reviewer** is automatically RFQA.

Anyway, core reviewers are invited to ask the review also of a non-core reviewer to spread knwoledge and give them an additional opportunity to learn.

### Labelling system

We suggest an appropriate use of the label system on PRs.
This help reviewers if the team scale up with more developers that usually will create more PRs.
The correct usage of labels can also be an effective system to highlight important note about the release of the PRs.

* **DO NOT MERGE**: The PR has some dependecies on other PRs or implementation. The label suggest that if merged, that PR can produce breakages. You should carefully mention and link the related external PRs.
* **Draft**: The PR is just for sharing idea, POC, proposals, learning purpose...

### Ready for QA

If your story didn't pass QA and go back to development you have to:

  1. Remove the Ready for QA label
  2. Commit changes
  3. Start the process again requiring just a **Core review**

### Enforce reviews

To enforce the review process as a best practice the setting 'Require pull request reviews before merging' in the 'Branch protection' settings of the repo should be always enabled.
