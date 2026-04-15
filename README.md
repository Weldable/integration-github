# @weldable/integration-github

GitHub issues, PRs, and repository actions for Weldable.

Part of the [Weldable](https://weldable.ai/) integration library — see [@weldable/integration-core](https://github.com/weldable/integration-core) for the full catalog.

## Install

```bash
npm install @weldable/integration-github @weldable/integration-core
```

`@weldable/integration-core` is a peer dependency and must be installed alongside this package.

## Usage

```ts
import integration from '@weldable/integration-github'

// List your repositories
const listRepos = integration.actions.find(a => a.id === 'github.list_user_repos')!

const repos = await listRepos.execute(
  { type: 'owner', sort: 'updated', per_page: 10 },
  ctx, // ActionContext from your Weldable-compatible host
)

// Create a release
const createRelease = integration.actions.find(a => a.id === 'github.create_release')!

const release = await createRelease.execute(
  {
    owner: 'weldable',
    repo: 'integration-core',
    tag_name: 'v1.1.0',
    body: '## What'\''s new\n\n- Added mock helpers for arrays',
  },
  ctx,
)

console.log(release.html_url) // https://github.com/weldable/integration-core/releases/tag/v1.1.0
```

## Contributing and releasing

See [CONTRIBUTING.md](https://github.com/weldable/integration-core/blob/main/CONTRIBUTING.md) in `@weldable/integration-core` for the development workflow and release process.

## License

MIT
