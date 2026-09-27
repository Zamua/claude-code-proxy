# Fork maintenance

Temporary fork of raine/claude-code-proxy, based on v0.1.42.
Branch: fix/silent-tool-completion. Upstream tracking: PR #122.

The Codex adapter accepts repeated successful empty completions after successful
tool results. Hook system messages and fully wrapped system-reminder blocks are
recognized. Completed task notifications and framed final subagent hand-backs
also permit a silent finish. Extra user text, failed tasks, and any failed tool
result prevent acceptance. Notification reports remain untrusted data, not
instructions or approval.
Do not weaken missing-terminal, interrupted-stream, or non-tool-tail protection.

Tests: `cargo test --lib providers::codex::tests`, then the full package checks.
The canonical deployment configuration is maintained separately in nix-config;
it adds local provider patches and enables the package test suite.
Use synthetic data only. Never commit authentication material or traffic captures.
Remove the fork pin once an upstream release includes equivalent tested behavior.
