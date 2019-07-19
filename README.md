# React Project Template

This project was created with create-react-app. The following enhancements were added:

- Eslint and Prettier formatter
- Added pre- and post-push hooks to run the unit tests.
  1. Save the local changes to a stash named `pre-push-stash`.
  2. Run the test. `CI=true` so that it runs all tests without requiring any user input.
  3. If the tests failed, pop the stash named `pre-push-stash` and return an error code.
  4. If the tests pass, the `post-push` hook is executed and the stash named `pre-push-stash` is popped.

```
in package.json:
  "hooks": {
      "pre-push": "git stash save pre-push-stash && CI=true npm test || (git stash pop $(git stash list | grep pre-push-stash | cut -d: -f1) && exit 1) ",
      "post-push": "git stash pop $(git stash list | grep pre-push-stash | cut -d: -f1)"
    }
```

- Added useful packages.
- Added a globalStyles.js file to store reusable style constants like e.g. color codes, font details etc.
- Folder structure: Store component code & style & test in a folder with the same name as the component.
- Code conventions: the default javascript code conventions were used.

## Setup Instructions

- `npm install`
- Search for the word "template" and rename to your project name.

## Further decisions to be taken

- CSS vs. styled components

## Bonus: A list of some good practices

### Git:

- Use [git pair](https://github.com/spinningarrow/git-pair) for commit message authors.
- Git commit message should have the following format "[#42] Commit message", where #42 is the card number associated to this commit.
