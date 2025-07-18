## Branches
---
**Core Branches**
Development branch: `trunk / dev / main`
Production branch: `production / release`
### Naming branches
- Use a prefix for each branch to indicate purpose
	- `feature/` - New features or functionality
	- `bugfix/` - Fixing bugs
	- `refactor/` - Improving code structure without changing functionality
	- `test/` - Writing and improving testing
	- `doc`/ - Documentation updates
	- `chore/` - Dev only tasks
- Use hyphens `-` to separate words

## Commits
---
### Naming commits
- Use a prefix for each commit
	- `feat` - new feature/functionality of the main feature
	- `fix` - bug fix
	- `docs` - documentation
	- `style` - formatting, no logic changes
	- `refactor` - code change that is not a fix or feature
	- `test` - adding or fixing tests
	- `chore` - CI, tooling
- **Example**: feat: implement email/password login
- Write imperative commit subjects
	- Good `implement email/password login`
	- Bad `Fixed bug`
- Tip: If done correctly, the subject will complete the sentence `If merged, this commit will...`

## Pull-Requests
---
Squash a merge commits when making a pull request. 
```
Work-in-progress commits are helpful when working on a feature branch, but they aren’t necessarily important to retain in the Git history. If you squash these commits into one commit when merging to the default branch, the changes are consolidated, leading to a clear Git history. - GitHub Official
```
Pull request summary text - Branch name
Pull request context text - Title of all squashed commits in order by date
## Version journey example
- Create branch of `develop`: `feature/anime-model`
	- Code and commit
		- `feat: create anime model`
		- `feat: create character model`
		- `chore: create migrations for anime/character model`
		- `test: anime model unit test`
		- `fix: anime model field requirements`
	- Squash: `feat: add anime model`
- Create another branch: `feature/user-anime-list`
	- Code and commit
		- `feat: create animeList model`
		- `chore: create migration for animeList model`
		- `feat: add animeList fk to user`
	- Squash: `feat: add animeList fk to user model`
- Pull request to `develop` branch
- History of `develop`:
	- `feat: add anime model` <- Pull request name
	- `feat: add animeList fk to user model` <- Pull request name