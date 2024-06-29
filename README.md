#  📦 tiny-inline-diagnostic.nvim

A Neovim plugin that display prettier diagnostic messages. Display one line diagnostic messages where the cursor is, with icons and colors.

## 🖼️ Images

![tinyinlinediagnostic-ezgif com-crop](https://github.com/rachartier/tiny-inline-diagnostic.nvim/assets/2057541/23744f2b-5e92-4fad-8a1c-1df9afa6a42b)

## 📥 Installation

With Lazy.nvim:

```lua
{
    "rachartier/tiny-inline-diagnostic.nvim",
    event = "VeryLazy",
    config = function()
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


