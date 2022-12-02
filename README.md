<div align="center">
  <h1>Transitive Docker Dependencies with rules_js</h1>
</div>

# Reproduction

**Requirements**

- Node.js
- pnpm (`npm install -g pnpm`)
- Bazelisk (`npm install -g @bazel/bazelisk`)

**Setup**

- `pnpm i` (Install Node dependencies)

**Works fine**

- `bazelisk run //:bin` (Run app)

**Transitive dependencies are not passed on to container**

- `bazelisk run //:image && docker run --rm -it bazel:image` (Run Docker container)

  ```
  Error: Cannot find module '@org/lib2'
  Error: Cannot find module '@faker-js/faker'
  ```
