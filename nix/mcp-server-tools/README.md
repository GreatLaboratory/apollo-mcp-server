# MCP Server Tools

This directory contains autogenerated nix evaluations for the various MCP server
tools for use during development.

## Adding More Servers

In order to add more server binaries to this autogenerated evaluation, do the
following:

1. Add the tool to the list of tools in `mcp-servers.json`

```json
{
  <EXISTING TOOLING>,
  "@modelcontextprotocol/server-<NAME OF SERVER>"
}
```

2. Regenerate the autogenerated files by running the following in the current
directory

```shell
$ node2nix -i mcp-servers.json --pkg-name nodejs_22 \
  -o node-generated/node-packages.nix \
  -c node-generated/default.nix \
  -e node-generated/node-env.nix
```

3. Reload your nix development shell
