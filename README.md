# Ollama Modelfile Syntax

VSCode/VSCodium extension providing syntax highlighting for [Ollama](https://ollama.com) Modelfiles.

## Features

- Highlights all Modelfile instructions: `FROM`, `PARAMETER`, `TEMPLATE`, `SYSTEM`, `ADAPTER`, `LICENSE`, `MESSAGE`, `REQUIRES`
- Highlights known `PARAMETER` names (e.g. `temperature`, `num_ctx`, `top_k`, ...)
- Highlights `MESSAGE` roles (`system`, `user`, `assistant`)
- Supports triple-quoted strings `"""..."""` (multiline, used in SYSTEM/TEMPLATE/LICENSE)
- Nested single-quoted strings inside double/triple-quoted strings: `"example 'quoted' word"`
- Go template expression highlighting inside `{{ }}` blocks (for TEMPLATE instruction)
- Line comments with `#`
- Numeric literals

## File Detection

The extension automatically activates for files matching:
- `Modelfile` (exact)
- `Modelfile.*` (e.g. `Modelfile.llama3`, `Modelfile.yaml`)
- `Modelfile-*` / `Modelfile_*`

## Example

```
# Example Modelfile
FROM llama3.2

PARAMETER temperature 0.8
PARAMETER num_ctx 4096
PARAMETER stop "<|eot_id|>"

SYSTEM """
You are a helpful assistant. 'Be concise' is your motto.
"""

TEMPLATE """
{{- if .System }}<|start_header_id|>system<|end_header_id|>
{{ .System }}<|eot_id|>{{- end }}
<|start_header_id|>user<|end_header_id|>
{{ .Prompt }}<|eot_id|>
<|start_header_id|>assistant<|end_header_id|>
{{ .Response }}<|eot_id|>
"""

MESSAGE user "Hello, how are you?"
MESSAGE assistant "I'm doing well, thanks for asking!"

LICENSE """
MIT License
"""
```

## Installation

### Local install (VSCodium / VSCode)

1. Package the extension:
   ```bash
   npm install -g @vscode/vsce
   vsce package
   ```
2. Install the generated `.vsix` file:
   - Open VSCodium
   - Open the Command Palette (`Ctrl+Shift+P`)
   - Run **Extensions: Install from VSIX...**
   - Select the `.vsix` file

### Open VSX Registry (VSCodium marketplace)

See [PUBLISHING.md](PUBLISHING.md) for steps to publish to the Open VSX Registry.

## License

MIT
