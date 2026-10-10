# chrome-extensions

A collection of awesome Chrome extensions by [Hacktoolkit](https://github.com/hacktoolkit).

- [GitHub JIRA](https://github.com/hacktoolkit/github-jira-chrome-extension) - Turns JIRA tags into clickable links in GitHub. For teams using JIRA.
- [Notes](https://github.com/hacktoolkit/notes-chrome-extension) - Take notes on URLs
- [Organize Tabs](https://github.com/hacktoolkit/organize-tabs-chrome-extension) - Organize your tabs!
- [Paywall X-ray](https://github.com/hacktoolkit/paywall-xray-chrome-extension) - Manipulates the DOM to see the content your browser has already downloaded
- [Skeleton](https://github.com/hacktoolkit/skeleton-chrome-extension) - Template for new extensions: Manifest V3, vanilla JS, tests, headless e2e, CI, holodeck

## Starting a new extension

Use the [skeleton-chrome-extension](https://github.com/hacktoolkit/skeleton-chrome-extension) template: Manifest V3, vanilla JavaScript, tests, headless e2e, CI and the holodeck dev profile, all wired up in a small working extension.

## Development

Each extension is a submodule with its own repository; work, branch and open pull requests there. Conventions for contributors and AI agents, including the throwaway **holodeck** browser profile used for all testing, are in [AGENTS.md](AGENTS.md).

```sh
git clone --recurse-submodules git@github.com:hacktoolkit/chrome-extensions.git
cd chrome-extensions/organize-tabs-chrome-extension
make help
```
