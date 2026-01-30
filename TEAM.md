## Team name: Byte Me

## Members:
* Martin Munck (@MMunck)
* Taavet Jukola (@KarVaneOrav)
* Lara Luks (@laracroft8)
* Margo Hütt (@margohu)
* Mai Raadik (@kaneelisuhkur)

## Team workflow:

### Branch naming convention
All feature branches follow a consistent naming pattern to make it easy to identify their purpose.

**Format:** `feature/BB-{issue-number}-{short-description}`

**Rules:**
- Always start with `feature/`
- Include the Jira issue number (BB-X)
- Add a brief description in kebab-case (lowercase with hyphens)
- Keep the description concise but meaningful
- Use descriptive words that explain what the branch does

**Examples:**
- ✅ `feature/BB-5-fix-estonian-placeholder`
- ✅ `feature/BB-7-add-product-validation`
- ✅ `feature/BB-8-enable-typescript-strict-mode`
- ❌ `fix-bug` (no issue number, too vague)
- ❌ `feature/BB-5` (missing description)

**Branching strategy:**
- All feature branches are created from `main`
- Never commit directly to `main` after initial setup
- Delete branches after they are merged

### Commit message convention
We follow a structured commit message format:

**Format:** `BB-{issue-number}: {Clear description of what was done}`

**Examples:**
- ✅ `BB-5: Replaced Estonian placeholder with English in README.md`
- ✅ `BB-7: Added validation annotations to ProductRequest DTO`
- ✅ `BB-8: Fixed TypeScript build errors in inventory page`
- ❌ `fixed bug` (too vague, no issue reference)
- ❌ `update` (not descriptive)

**Rules:**
- Always reference the Jira issue number (BB-X)
- Use present tense ("Add feature" not "Added feature")
- Be specific about what was changed
- Keep it under 72 characters when possible
- First line is the summary, add details in the body if needed

### Pull request process
1. Create feature branch from `main`
2. Make multiple commits (minimum 2 per feature)
3. Push branch to GitHub
4. Open Pull Request with clear description
5. Assign at least one reviewer
6. Address review comments
7. Merge using agreed strategy (see below)
8. Delete branch after merge

### Merge Strategies
We use different merge strategies depending on the situation:
- **Merge Commit**: For features with meaningful commit history
- **Squash Merge**: For small fixes or when commits are messy

### Code Review Guidelines
- Reviewers must leave comments
- Authors must respond to all comments
- Request changes if needed
- Approve when satisfied

## Team vision
**We commit, request and review. We win**
