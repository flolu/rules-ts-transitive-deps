<div align="center">
  <h1>rules_ts transitive dependencies</h1>
</div>

# Reproduction

**Requirements**

- Node.js
- pnpm (`npm install -g pnpm`)
- Bazelisk (`npm install -g @bazel/bazelisk`)

**Setup**

- `pnpm i` (Install Node dependencies)

**Error**

- `bazelisk run //:bin` (Run app)
