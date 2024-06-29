#  📦 tiny-inline-diagnostic.nvim

A Neovim plugin that display prettier diagnostic messages. Display one line diagnostic messages where the cursor is, with icons and colors.

## 🖼️ Images

![tinyinlinediagnostic](https://github.com/rachartier/tiny-inline-diagnostic.nvim/assets/2057541/6a6eb093-f473-4e61-b344-08317c6b78e9)

## 🛠️ Setup

- You need to set `vim.opt.updatetime` to trigger `CursorEvent` faster (ex: `vim.opt.updatetime = 100`)
- You also need to set `vim.diagnostic.config({ virtual_text = false })`, to not have all diagnostics in the buffer displayed.

## 📥 Installation

With Lazy.nvim:

```lua
{
    "rachartier/tiny-inline-diagnostic.nvim",
    event = "VeryLazy",
    config = function()
        vim.opt.updatetime = 100
        require('tiny-inline-diagnostic').setup()
    end
}
```

## ⚙️ Options

```lua
-- Default configuration
require('tiny-inline-diagnostic').setup({
        signs = {
            left = "",
            right = "",
            diag = "●",
            arrow = "    ",
        },
        hi = {
            error = "DiagnosticError",
            warn = "DiagnosticWarn",
            info = "DiagnosticInfo",
            hint = "DiagnosticHint",
            arrow = "NonText",
            background = "None", -- Should be "None" or a hexadecimal color (#RRGGBB)
        },
        blend = {
            factor = 0.27,
        },
        options = {
            clear_on_insert = false,
        }
})
```

## 💡 Highlights

- TinyInlineDiagnosticVirtualTextError
- TinyInlineDiagnosticVirtualTextWarn
- TinyInlineDiagnosticVirtualTextInfo
- TinyInlineDiagnosticVirtualTextHint
- TinyInlineDiagnosticVirtualTextArrow

`Inv` is used for left and right signs.
- TinyInlineInvDiagnosticVirtualTextError
- TinyInlineInvDiagnosticVirtualTextWarn
- TinyInlineInvDiagnosticVirtualTextInfo
- TinyInlineInvDiagnosticVirtualTextHint

## 📚 API

- `require("tiny-inline-diagnostic").change(background, factor)`: change the background color and the blend factor, useful if you want to change the colorscheme on the fly.
- `require("tiny-inline-diagnostic").get_diagnostic_under_cursor api(bufnr)`: get the diagnostic under the cursor, useful if you want to display the diagnostic in a statusline.

## ❓ FAQ:

- **Q**: It takes a long time for the diagnostic to appear:
    - You need to set `vim.opt.updatetime = 100` (or any number in ms). It will trigger the `CursorHold` event faster.
- **Q**: All diagnostics are still displayed
    - You need to set `vim.diagnostic.config({ virtual_text = false })` to remove all the others diagnostics.
