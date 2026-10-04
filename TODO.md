# TODO

## DNS configuration safety

- [ ] Replace the current `sudo tee` overwrite with a deliberate, failure-safe configuration flow; never modify system DNS configuration without checking compatibility and obtaining the required privileges.
- [ ] Detect the operating system and network-management setup before making changes. For Debian variants, verify that `/etc/resolv.conf` exists and determine whether it is a regular file, symlink, or managed by another service.
- [ ] Before any supported system-level change, create and verify a recoverable backup of the existing resolver configuration. Define how and when the original configuration is restored, including on errors and normal shutdown.
- [ ] Detect relevant network and resolver services and their state. Coordinate with the active manager rather than unexpectedly stopping or overwriting its configuration; fail safely when the setup is unsupported.
- [ ] Handle expected failures clearly, including missing files, insufficient permissions, unsupported distributions, backup or write failures, and interruption.
- [ ] Prefer an isolated, temporary resolver configuration for contained testing instead of changing the host's system-critical resolver file. Document the limits of this approach and how it is cleaned up.

## Usability and project direction

- [ ] Correct the Python script's shebang and document supported invocation methods.
- [ ] Evaluate whether a Bash implementation is appropriate for the intended Linux-only use, or whether Python's portability and maintainability justify keeping it.
- [ ] Consider an optional interactive mode while preserving automatic DNS rotation for users who want it.
- [ ] Clearly disclose that DNS servers are selected and changed automatically every five minutes, what system configuration is affected, and that DNS rotation alone does not guarantee privacy or anonymity.
- [ ] Document that use is intended for authorized, controlled testing, and provide setup, verification, recovery, and cleanup instructions.
