# CFC Pain Point Research - System Design Improvements

- Based on conversations with Jeff Doolittle, he asserts system architects are pain doctors and must find ways to relieve the pain. The following are notes on pain investigation within CFC to help uncover pain points in architecture, system processees and to rank them on effort, risk and value

## Pain Points

Situation:

Then:

- Mono Repo - We are on a mono repo with about 6 teams and there are quite a few mini projects with the repo
- Git strategy/Code review - Sort of trunk based, the code reviews are treated as rubber stamps due to lack of standards
- Fragmented code deploy strategy - Each project has its own build pipeline and promotion strategy to the upper environments
- Unstable upper environments - Our dev and qa environments are broken, its very hard to test

Now:

- We have decided to start moving away from a mono repo on a per project basis
- Git/PR: Myself and few others have created and working to socialize code review guidelines (not sure how to best get adoption and make the guidelines more visible apart of the workflow)
- CODE Deploy - Each project still has their own pipelines but we have started standardizing the build templates for all apps making it easier to create a pipeline. We still have too many pipelines (one per stage)
- A team of us have completely created the entire cloud resources into infrastructure as code

Still pain points:

- Creating a culture where PRs are fun, a learning opportunity etc
- Still working on staging and new production environments and the deployment strategy for those
- Regarding the development cycle there is and has been a lot of churn because our stories are not fully vetter or refeined and so we have a problem sizing work and delivering on it. Currently got promoted and working a people process to help create better stories before work starts. Any advice here?
