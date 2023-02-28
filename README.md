# lsp_lines.nvim

`lsp_lines` is a simple neovim plugin that renders diagnostics using virtual
lines on top of the real line of code.

![A screenshot of the plugin in action](https://user-images.githubusercontent.com/45848083/221947803-765a26d0-8cc3-437a-8605-b4ef157c020f.png)

Font is [Fira Code](https://github.com/tonsky/FiraCode), a classic\
Theme is [tokyonight.nvim](https://github.com/folke/tokyonight.nvim)

## Background

LSPs provide lots of useful diagnostics for code (typically: errors, warnings,
linting). By default they're displayed using virtual text at the end of the
line which is in many cases good enough, but often there's more than one
diagnostic per line. It's also quite common to have more than one diagnostic
per line, but again, there's no handy way to read the whole thing.

`lsp_lines` solves this issue.

## Installation

### With packer.nvim

```lua
use "edr3x/lsp_lines.nvim"
```

And then in `init.lua`

```lua
require("lsp_lines").setup()
```

### With Lazy.nvim

```lua
{ "edr3x/lsp_lines.nvim", opts = {} }
```
___

> Note:\
> It is recommended to also remove the regular virtual text diagnostics to avoid pointless duplication:
> ```lua
> vim.diagnostic.config({ virtual_text = false })
> ```

## Usage

You can set keymap to toggle

```lua
vim.keymap.set(
  {"n", "x"},
  "<leader>l",
  require("lsp_lines").toggle,
  { desc = "Toggle lsp_lines" }
)
```

If you are using lazy.nvim you can simply do:

```lua
{
    "edr3x/lsp_lines.nvim",
    keys = {
        {
            "<leader>l",
            function()
                require("lsp_lines").toggle()
            end,
            desc = "Toggle lsp_lines"
        }
    },
    opts = {}
}
```

## Contributing

- Discussion or patches: ~whynothugo/lsp_lines.nvim@lists.sr.ht
- Bugs / Issues: https://todo.sr.ht/~whynothugo/lsp_lines.nvim
- Tips: https://ko-fi.com/whynothugo

## Development

It would be nice to show connecting lines when there's relationship between
diagnostics (as is the case with `rust_analyzer`). Oh perhaps surface them via
hover().

## Licence

This project is licensed under the ISC licence. See LICENCE for more details.
