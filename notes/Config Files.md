## Lunarvim

```lua
-- install plugins
lvim.plugins = {
  "stevearc/dressing.nvim",
  "folke/trouble.nvim",
  "nvim-tree/nvim-web-devicons",
  "sainnhe/sonokai",
  {
    "phaazon/hop.nvim",
    event = "BufRead",
    config = function()
      require("hop").setup()
      -- setup hop
      vim.api.nvim_set_keymap("n", "s", ":HopChar1<cr>", { silent = true })
      vim.api.nvim_set_keymap("n", "S", ":HopWord<cr>", { silent = true })
    end,
  },
  {
    "zbirenbaum/copilot-cmp",
    event = "InsertEnter",
    dependencies = { "zbirenbaum/copilot.lua" },
    config = function()
      vim.defer_fn(function()
        require("copilot").setup()     -- https://github.com/zbirenbaum/copilot.lua/blob/master/README.md#setup-and-configuration
        require("copilot_cmp").setup() -- https://github.com/zbirenbaum/copilot-cmp/blob/master/README.md#configuration
      end, 100)
    end
  },
}

lvim.builtin.dap.active = false
lvim.builtin.alpha.active = false
lvim.builtin.lir.active = false
lvim.builtin.bigfile.active = false
lvim.builtin.project.active = false
lvim.builtin.terminal.active = false
lvim.builtin.illuminate.active = false
lvim.builtin.breadcrumbs.active = false
lvim.builtin.which_key.active = false
lvim.builtin.theme.active = false
-- lvim.builtin.bufferline.active = false

-- setup black formatting
local formatters = require "lvim.lsp.null-ls.formatters"
formatters.setup { { name = "black" }, }
lvim.format_on_save.enabled = true

-- quick save
lvim.keys.normal_mode["<leader>w"] = ":wa<CR>"

-- setup nvim-tree
lvim.builtin.nvimtree.setup.git.enable = true
lvim.builtin.nvimtree.setup.git.ignore = true
lvim.builtin.nvimtree.setup.update_cwd = false
lvim.builtin.nvimtree.setup.actions.change_dir.enable = false

-- setup telescope
lvim.keys.normal_mode["<leader>f"] = false
lvim.keys.normal_mode["<leader>ff"] = ":Telescope find_files<CR>"
lvim.keys.normal_mode["<leader>fc"] = ":Telescope colorscheme<CR>"
lvim.keys.normal_mode["<leader>fo"] = ":Telescope oldfiles<CR>"

-- setup tabline
lvim.keys.normal_mode["<leader><leader>"] = false
lvim.keys.normal_mode["<Tab>"] = ":BufferLineCycleNext<cr>"
lvim.keys.normal_mode["<S-Tab>"] = ":BufferLineCyclePrev<cr>"
lvim.keys.normal_mode["<leader><leader>"] = ":BufferLinePick<cr>"
lvim.keys.normal_mode["<leader>o"] = ":BufferLineCloseOthers<cr>"
lvim.keys.normal_mode["<leader>x"] = ":BufferKill<cr>"
lvim.keys.normal_mode["<leader>q"] = ":close<cr>"

-- setup colorscheme
lvim.colorscheme = "sonokai"

-- setup lunarvim
lvim.keys.normal_mode["<leader>lc"] = ":e ~/.config/lvim/config.lua<cr>"
lvim.keys.normal_mode["<leader>lu"] = ":LvimUpdate<cr>"

-- setup nvim-tree
lvim.keys.normal_mode["<leader>e"] = ":NvimTreeToggle<cr>"

-- setup lsp
lvim.lsp.buffer_mappings.normal_mode['<leader>r'] = { vim.lsp.buf.rename, "rename" }

-- setup trouble
lvim.keys.normal_mode["<leader>d"] = ":TroubleToggle document_diagnostics<cr>"

-- disable highlight
lvim.keys.normal_mode["<leader>h"] = ":noh<cr>"
```
