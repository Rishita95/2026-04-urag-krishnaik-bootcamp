# 2026-04-urag-krishnaik-bootcamp

## Essential Commands for Working in this Project

To ensure a smooth development experience and consistency across environments, everyone working on this project should be familiar with the following commands.

### Managing Tools with `mise`

This project uses `mise` to manage local tool dependencies. You can easily install tools and save them to your `mise.toml` by specifying their name and desired version, such as `@latest` or `@20.12.0`. If you want to automatically resolve the newest available version and immediately hardcode (pin) that exact version number for stability, use the `--pin` flag. To keep your environment up to date later, use `mise upgrade` to update within the ranges currently specified in your configuration, or `mise upgrade --bump` to grab the absolute newest versions available and bump your settings *(Note: `--bump` preserves version precision. If a tool is set to `"latest"`, it will remain `"latest"`. To convert "latest" to a pinned version, you must use `mise use --pin <tool>@latest`)*. To remove a tool from your configuration, use `mise unuse <tool>`. Keep in mind that removing a tool from `mise.toml` does not delete the downloaded files; run `mise prune` to delete unused binaries and free up disk space.

```bash
# Example 1: Install (sync) all tools defined in the project's mise.toml
mise install

# Example 2: Add a single tool
mise use node@latest

# Example 3: Add multiple tools at once
mise use node@latest "npm:meta"@latest tilt@latest uv@latest

# Example 4: Pin multiple tools to their exact newest versions
mise use --pin node@latest "npm:meta"@latest tilt@latest uv@latest

# Example 5: Upgrade tools within their currently specified ranges
mise upgrade

# Example 6: Upgrade all tools to the absolute newest versions and bump configurations
mise upgrade --bump

# Example 7: Remove a tool from your configuration
mise unuse node

# Example 8: Clean up disk space by deleting tools no longer listed in configuration
mise prune
```

### Managing Multiple Repositories with `meta`

This project is configured as a meta-repository to manage multiple related sub-projects seamlessly. We use the `meta` CLI tool to execute `git` commands across all sub-projects at once. You can easily expand `meta`'s capabilities by installing plugins (like `meta-gh` for GitHub integration) using `npm` (see the [full list of available plugins](https://github.com/mateodelnorte/meta#available-plugins)). To see which plugins are currently installed and active, run `meta --help` and check the 'Commands' section. After cloning the root repository, initialize and clone all sub-projects with `meta git clone`. You can check the status of all repositories simultaneously using `meta git status`, fetch and merge the latest changes in one go with `meta git pull`, or perform bulk branch switches across the entire project with `meta git checkout <branch>`.

```bash
# Example 1: Add a meta plugin (like meta-gh) via npm for extended features
npm install -D meta-gh

# Example 2: List installed meta plugins (shown under 'Commands')
meta --help

# Example 3: Clone and initialize all sub-projects
meta git clone

# Example 4: Check the status of all repositories
meta git status

# Example 5: Pull the latest changes across all repositories
meta git pull

# Example 6: Switch branches across all repositories
meta git checkout main
```
