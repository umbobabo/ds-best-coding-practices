# CI/CD
CI is straightforward and stands for continuous integration, a practice that focuses on making preparing a release easier. But CD can either mean continuous delivery or continuous deployment, and while those two practices have a lot in common, they also have a significant difference that can have critical consequences for a business.

## Continuous integration
Developers practicing continuous integration merge their changes back to the main branch as often as possible. The developer's changes are validated by creating a build and running automated tests against the build. By doing so, you avoid the integration hell that usually happens when people wait for release day to merge their changes into the release branch.

Continuous integration puts a great emphasis on testing automation to check that the application is not broken whenever new commits are integrated into the main branch.

## Continuous delivery
Continuous delivery is an extension of continuous integration to make sure that you can release new changes to your customers quickly in a sustainable way. This means that on top of having automated your testing, you also have automated your release process and you can deploy your application at any point of time by clicking on a button.

In theory, with continuous delivery, you can decide to release daily, weekly, fortnightly, or whatever suits your business requirements. However, if you truly want to get the benefits of continuous delivery, you should deploy to production as early as possible to make sure that you release small batches, that are easy to troubleshoot in case of a problem.

## Continuous deployment
Continuous deployment goes one step further than continuous delivery. With this practice, every change that passes all stages of your production pipeline is released to your customers. There's no human intervention, and only a failed test will prevent a new change to be deployed to production.

Continuous deployment is an excellent way to accelerate the feedback loop with your customers and take pressure off the team as there isn't a Release Day anymore. Developers can focus on building software, and they see their work go live minutes after they've finished working on it.

## CI / CD Pipeline Example
[!Pipeline](https://github.com/sandeepasrani/ds-best-coding-practices/blob/CICD/CI-CD.png)

## CI/CD Expectations
- Unit & Integration Tests should run at every commit
- Reports of the Tests should be exposed by the system
- Logs should be clear and concise so that developers can understand what is wrong to fix it
- There should be a minimum 3 environments specifically dev/stage or prod as minimum or alpha/beta or stage builds
- The build pipeline should be clean and concise
- The pipeline should be reviewed with the entire team and agreed on

## Interesting reads
https://www.infoworld.com/article/3113680/devops/5-common-pitfalls-of-cicd-and-how-to-avoid-them.html
https://blog.gds-gov.tech/that-ci-cd-thing-principles-implementation-tools-aa8e77f9a350
