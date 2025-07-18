# tree-sitter-tolk

Tolk grammar for [tree-sitter](https://github.com/tree-sitter/tree-sitter).

Based on https://github.com/akifoq/tree-sitter-func, but actually almost rewritten.

## How to update and test grammar

You should update `grammar.js` and/or `grammar/` folder (required from js).
Folders `src`, `bindings`, `build`, and files `binding.gyp`, `Cargo.toml` are auto-generated by tree-sitter.

After updating grammar, run

```bash
tree-sitter generate
```

(will change `src/`).

To manually test, create `tmp.tolk` with some content, and run

```bash
tree-sitter parse tmp.tolk
```

and manually inspect the output.

If you introduce new keywords, also modify `queries/highlights.scm`.
This file is not needed for VS Code, but

```bash
tree-sitter highlight tmp.tolk
```

produces colored output, just a pleasant feature, so keep this file up to date also.

Finally, to build wasm, run **in the project folder**

```bash
yarn grammar:wasm
```

This is executed in Docker and may take a long time for the first run.
On finish, `tree-sitter-tolk.wasm` will be saved into the `server/` folder.

Don't forget to run/update JS tests after modifying grammar!
