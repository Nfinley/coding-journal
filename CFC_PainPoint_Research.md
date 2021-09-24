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
- Git branching strategies
- Current environment landscape
- Releasing code to production
- Build/Release pipeline speed and organization (ie how to cache node modules for reuse)
- Social aspects, team buiding

Current branching strategy

Intermediate bridge strategy

1. One proposal for Branching and deployment (tied together) - dev (main line) and cherry pick into a QA branch which is deployed to QA env and then cherry picked into Staging then merged into Production (on the master branch)
   1. Reservations with this is the Cherry picking seems like it would get really messy

Dream state

- Terraform
- Feature Flags (further)

What are we currently doing

- mono repo with different sub directories for each project
- multiple teams work of different directories
- we release continuously to CI and then very randomly to upper environments (not consistant)

Why doesn't it work

- Currently it doesn't work because when someone wants to release on say app and there a a tone of changes before last prod release and we can't confidently verify these changes

What needs to happen to make it work

- Consolidate all work in both branches

- Type of git workflow trunk based or multiple branches

* Short term solution until we release new features of player and learn to world
  - Have one branch where fixes for current production are fixed and then cherry picked into new teams long running branch
  - Have a the new long running branch where all of the terraform work is happening and migrate all teams working on new content to this branch (continue with trunk based and beef up automated processes)

### MEETING NOTES 1/6

Max: - Get something that works to fix our current deployment and git issues now - Don't worry about the complexity, we can train or automate

- Trunk based

- Adding Processes:
  - Quicker PR review
  - Accountability for PRS (maybe owners per directory)
  - How to reduce noise in mono repo

Issues:

## Separation of Library and Curriculum concerns

- There are current issues with mixing concerns of library component inside ss-components and the curriculum components

## Data test Id issues

### Solution 1: On every component that needs it we include a specific `data-testid` as a prop and it gets passed to its respective base component. On each base component we set an attribute for `data-testid` and have a default set

**Pros:**

- Will have a unique `data-testid` on it to indicate to the user what it is, which gives us uniqueness per component
- Will have less frivoulous components that are thin wrappers with no additional styles or functionality
- We are already doing this more (passing in data-testid) than option #2

**Cons:**

- Additional prop to pass
- Component name may not be specifically named

Example:

```javascript
<TertiaryButton
  data-testid="create-a-class" //Need to figure our naming convention
  disabled={props.limitReached}
  onClick={this.handleCreate}
>
  Create a Class
</TertiaryButton>

const TertiaryButton = styled(Button).attrs(props => ({
  plain: true,
}))``

TertiaryButton.propTypes = {
  icon: PropTypes.node,
  label: PropTypes.string.isRequired,
  onClick: PropTypes.func.isRequired,
}

TertiaryButton.defaultProps = {
  data-testid: 'tertiaryBtn'
}
```

### Solution 2: Components house their own data-testid internally and no prop is passed down (current way) and you create a new instance of a base component to add

**Pros:**

- They are hidden from the user
- One less prop to pass down
- With new instances created the component is named explicity

**Cons:**

- We cannot control the uniqueness of the ids and we ultimately need to and should
- By not controlling uniqueness there would be collisions, which when address accessability this would be a problem
- When we create new instances of the base components (Tertiary Button => CreateAClassButton) we are not adding any new functionality or style, could be huge component bloat

Example:

```javascript
// When using
<CreateAClassButton disabled={props.limitReached} onClick={this.handleCreate}>
  Create a Class
</CreateAClassButton>;

// Actual file:
const CreateAClassButton = styled(TertiaryButton).attrs({
  "data-testid": "create-a-class-btn",
  icon: <AddIcon />
})``;
```

### Rubric to create a new implementation of a library base component:

1. Does what you are creating have new business logic or functionally that is not achieved by your base component?
2. Does what you are creating have additional styling needs?

If neither of these are true then use the basecomponent from the library (assuming we go with number #1 proposed above)

Use link as library and download link as example

### When to include a component in the library vs. into an application

1. Is your component generic?
2. Could it be used by more than one application (ie App, Learn, etc)?

If the answer is yes then its a library component if its not it should live in its application. The more we lean to specific then it should live in the application. Think of it in terms of atoms (single pieces - a button), molecules (a few pieces put together - a button and search input with label) and organisms (multiple pieces together like an entire header component). The library we are creating should consist mostly of atoms (a button, a link) and possibly some molecules. Then each application composes all of these atoms into molecules and organisms or as we are calling them experience components. [Atomic Design by Brad Frost](https://bradfrost.com/blog/post/atomic-web-design/)
