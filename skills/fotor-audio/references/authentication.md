---
platform: kimi
---

# Kimi Code authentication and browser routes

## Native package and skills

Kimi Code CLI and Kimi Code Desktop share this script-free Fotor package. The
native manifest declares production HTTP MCP and OAuth, with complete tool
discovery. User permissions and native tool restrictions remain authoritative.
Discover the actual tool schema before use; a missing tool is not by itself
evidence of expired authorization. Follow the workflows in
[MCP integration](mcp-integration.md#runtime-workflow).

Use the installed plugin's skills and native file reader. Explicit invocation is
plugin-qualified, for example `/skill:fotor:fotor-connect`. Resolve reference
files within the current skill directory; a new session or native reload may be
needed after installation. CLI and Desktop can share a user home and plugin
inventory while running different embedded core versions.

## Native OAuth and completion

Model login, Fotor MCP authorization and website cookies are separate states.
Use Kimi's native MCP settings or the plugin-derived authorization tool. Verify
the actual service name; the tested name is `plugin-fotor:fotor`, and the CLI
entry is `/mcp-config login plugin-fotor:fotor`. Keep one plugin-owned Fotor
service instead of adding a manual duplicate.

Reuse valid authorization. When the client confirms that consent is needed,
start one native flow in an ordinary external browser and let the user complete
it. Follow the shared [OAuth completion choice](mcp-integration.md#oauth-completion-choice)
before further operations. Verify client completion, callback shutdown, discovered
tools and the requested authenticated operation; a browser success page alone
does not prove that the client connected.

The inspected native human authorization wait is at most fifteen minutes. Apply
the shared [bounded recovery](mcp-integration.md#bounded-connection-recovery) budget
to automatic connection and callback completion, including observed host retries.
Cancellation, denial, timeout or a callback-close step that remains pending stops
that flow. Use native cancellation and report the outcome; repeated authorization
must not extend an exhausted wait. Do not read, copy or reset credentials to
diagnose a network or installation problem.

## Website routes

OAuth always uses an ordinary external browser. For a user-requested website
connection, prepare the intended browser before obtaining the one-time link:

| Client | Website route |
| --- | --- |
| Kimi Code CLI | The user's ordinary external browser, opened through an available native capability or a properly quoted single shell command with the host's required permission |
| Kimi Code Desktop | The native built-in browser; confirm its own current website state rather than assuming it shares external-browser cookies |

WebBridge is optional and is not a Fotor dependency. If the requested native route
is unavailable, explain the limitation and obtain the user's route choice before
using a fallback. Keep automatic and manual openings distinct. Preserve all
existing browser sessions; never switch to private/incognito mode, log the user
out or clear browser data as a connection step.

Follow [website connection](mcp-integration.md#connect-to-the-website): request one
handoff link, check its production origin and expiry, open the original URL once,
and wait for the user's result. Do not prefetch, rewrite or repeat-consume it.
An existing website session is an existing-session handoff, not a first login.
Do not open the website merely because the plugin was installed or MCP connected.

## Updates, removal and credential ownership

Install and replace the complete package through Kimi's native plugin manager.
Local installation copies its source; editing the source directory does not
update the installed copy. Start a new session or reload and verify the actual
version, paths, skill namespace and tool inventory. Local replacement and
GitHub-native update are different checks.

Keep the plugin identity and production service configuration stable when
replacing the previous trial. Preserve account/model settings, native user
overrides and real grants. Native removal can leave managed files and credential
state; it is not a revocation or proof of complete cleanup. A reinstall still
needs a new connection, which may reuse valid authorization without new consent.
Two clients sharing a grant do not constitute two independent first logins.

## Known host risks

The tested CLI 2.3.3 and Desktop 1.1.4 with embedded core 2.3.2 have documented
limitations. Fault-injection tests showed that one assistant invocation could
be sent again after a lost response: synthetic image submission, upload-URL and
website-link operations were accepted twice, or three times under repeated
failure. Native retries can occur below the assistant's visible call history.
No actual duplicate Fotor generation or charge was established by those tests;
video replay was not separately measured. Do not infer service-side deduplication.

A separate conditional OAuth test held an idle callback connection open. The
completion request finished only after that connection closed; the code-wait
timeout did not bound the later listener-close stage. Ordinary production OAuth
also succeeded, which does not demonstrate that this fault branch is fixed.

These are versioned host-risk disclosures, not a stage whitelist. Full tool
discovery remains enabled. Preserve the normal pre-submission credit notice,
user budgets and permissions, and the shared prohibition on assistant resubmission
when the outcome is unknown. This note adds no repeated per-request Kimi warning
or blanket confirmation step. Report uncertain outcomes honestly.

An upstream change or a successful ordinary call does not remove these findings.
Verify the actually installed CLI and Desktop core, then rerun the affected
regression before updating the applicable risk record. Do not upgrade either
client automatically.

Sources: [native tool retry implementation](https://github.com/MoonshotAI/kimi-code/blob/ec495f0cb00f6db9a9118bf979112886f4264a41/packages/agent-core-v2/src/agent/mcp/tools/mcp.ts),
[native OAuth callback handling](https://github.com/MoonshotAI/kimi-code/blob/ec495f0cb00f6db9a9118bf979112886f4264a41/packages/agent-core-v2/src/mcpCore/oauth/callback-server.ts),
and [Desktop browser routes](https://www.kimi.com/code/docs/en/kimi-code-desktop/built-in-browser.html).
