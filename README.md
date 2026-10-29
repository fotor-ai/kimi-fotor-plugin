# Fotor for Kimi Code

<p align="center"><img src="assets/logo.svg" width="72" alt="Fotor logo" /></p>

<p align="center">
  <img src="https://img.shields.io/static/v1?label=version&amp;message=0.7.0&amp;color=087f8c&amp;style=flat-square" alt="Version" />
  <img src="https://img.shields.io/static/v1?label=channel&amp;message=production&amp;color=238636&amp;style=flat-square" alt="Release channel" />
  <a href="LICENSE"><img src="https://img.shields.io/static/v1?label=license&amp;message=Apache-2.0&amp;color=57606a&amp;style=flat-square" alt="Apache-2.0 license" /></a>
</p>

Use Fotor's shared skills with Kimi Code CLI and Desktop through native HTTP MCP
and OAuth. This complete root package is independently distributed from
[fotor-ai/kimi-fotor-plugin](https://github.com/fotor-ai/kimi-fotor-plugin). Verify that the selected channel has
actually been published before using a GitHub installation command.

| Field | Value |
| --- | --- |
| Plugin | `fotor` |
| Version | `0.7.0` |
| Release channel | `production` |
| MCP endpoint | `https://mcp.fotor.com/mcp` |
| Client baselines | CLI 2.3.3; Desktop 1.1.4 with separately recorded embedded core |

## Features and verification

The five skills cover connection/model queries, images, video, uploads and account
credits. The manifest enables native discovery of the complete service tool list,
subject to user permissions. Shared workflows use actual tool schemas and retain
the ordinary pre-submission credit notice. No bridge, installation hook or plugin
runtime is required.

Package checks cover files, references, and configuration. Verify installation, MCP authorization and calls, website login, credit links, uploads, and media execution separately in the selected host and environment. A release or model query does not establish successful website login or completed media results.

Known limitations in the tested host versions, including transport replay and
conditional OAuth callback completion, are documented in the
[Kimi authentication reference](skills/fotor-connect/references/authentication.md#known-host-risks).
Providing media instructions and tools does not mean every media operation was
tested live. Review the installed version's acceptance scope separately.

<a id="kimi"></a>

## Kimi Code

### Kimi installation

#### Production release

Use this GitHub source only after the selected channel is published and contains the root Kimi manifest. In the native CLI session, run:

```text
/plugins install https://github.com/fotor-ai/kimi-fotor-plugin
/plugins
```

Desktop uses Settings → Plugins → Add plugin with the same source. Review native trust and enable controls. A bare GitHub source selects the latest Release, falling back to the default branch only when no Release exists; inspect the resolved ref and package version.

Local acceptance can install the complete package directory with the same native
installer. Installation does not require model relogin or manual MCP entries.
Record the source and existing enabled state; preserve valid user settings.

### Kimi skills and native connection

Start a fresh session or native reload. Verify plugin `fotor`, version
**0.7.0**, the current skill directories and one plugin-owned service.
Explicit skills are qualified, for example `/skill:fotor:fotor-connect`.
The actual service name in the tested clients is `plugin-fotor:fotor`; use native
MCP status/settings and `/mcp-config login plugin-fotor:fotor` when consent is
required. Reuse existing grants. Follow the
[authentication guide](skills/fotor-connect/references/authentication.md)
and the shared OAuth completion choice before further operations.

### Kimi website and credits

OAuth uses a normal external browser. For a requested website handoff, CLI uses
the user's ordinary external browser and Desktop uses its built-in browser.
Prepare the chosen browser first, preserve its session, request one handoff link
and open it unchanged once. Ask the user to confirm the result; separate manual
fallback and an already signed-in website from automatic opening or first login.
WebBridge is not required by Fotor.

Credit queries return the actual balance. The common credit workflow can deliver
a validated pricing link for low balance or an explicit top-up request; payments
remain with the user. Balance-only instructions suppress the link and do not open
a browser. See the [credit workflow](skills/fotor-connect/references/credits.md).

### Kimi updates and removal

Record the source before using the native plugin manager's update, enable/disable
or removal controls. For a local source, reinstall the complete changed directory
and verify a new session; this is local replacement, not GitHub-native upgrade.
For GitHub, a bare source tracks the latest Release; an explicit branch tracks its
commits. Explicit Tags/commits remain pinned. Verify actual version and files even
after a successful update message.

Uninstall/reinstall and source changes preserve the native account configuration
and grants. Native removal can retain managed files and is not grant revocation.
Do not reset credentials, change the service or patch installation caches as a
routine update step. Stop and diagnose a duplicate Fotor service or unknown source.

### Kimi release channels

#### Production release

Use this GitHub source only after the selected channel is published and contains the root Kimi manifest. In the native CLI session, run:

```text
/plugins install https://github.com/fotor-ai/kimi-fotor-plugin
/plugins
```

Desktop uses Settings → Plugins → Add plugin with the same source. Review native trust and enable controls. A bare GitHub source selects the latest Release, falling back to the default branch only when no Release exists; inspect the resolved ref and package version. Record the current source, then replace it through native plugin management. Preserve account configuration and grants, and verify one Fotor installation in a new session.

#### Test release

Use this GitHub source only after the selected channel is published and contains the root Kimi manifest. In the native CLI session, run:

```text
/plugins install https://github.com/fotor-ai/kimi-fotor-plugin/tree/release/test
/plugins
```

Desktop uses Settings → Plugins → Add plugin with the same source. Review native trust and enable controls. A bare GitHub source selects the latest Release, falling back to the default branch only when no Release exists; inspect the resolved ref and package version. Record the current source, then replace it through native plugin management. Preserve account configuration and grants, and verify one Fotor installation in a new session.


## Workflows

Read [MCP workflows](skills/fotor-connect/references/mcp-integration.md#runtime-workflow),
[media preparation](skills/fotor-connect/references/media-upload.md) and
[credits](skills/fotor-connect/references/credits.md) for the matching request.
Every skill carries its own four runtime references; no repository or sibling
skill is needed to read them.

## Contents and license

`kimi.plugin.json`, `skills/`, `assets/logo.svg`, this guide and [LICENSE](LICENSE)
form the complete script-free package. The multi-platform repository documents
this external source rather than carrying another installable Kimi copy.
