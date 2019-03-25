vim-instant-markdown
====================
Want to instantly preview finnicky markdown files, but don't want to leave your favorite editor, or have to do it in some crappy browser textarea? **vim-instant-markdown** is your friend! When you open a markdown file in vim, a browser window will open which shows the compiled markdown in real-time, and closes once you close the file in vim.

As a bonus, [github-flavored-markdown][gfm] is supported, and styles used while previewing are the same as those github uses!

[![Screenshot][ss]][ssbig]

Installation
------------
You first need to have node.js with npm installed. Then:

`git clone https://github.com/twidxuga/instant-markdown-d`
`cd instant-markdown-d`
`[sudo] npm -g install`

- If you're on Linux, ensure the following packages are installed:
  - `xdg-utils`
  - `curl`
  - `nodejs-legacy` (for Debian-based systems)
- If you're on Windows, you may need to install [cURL][curl] and put it on your `%PATH%`.
- Copy the `after/ftplugin/markdown/instant-markdown.vim` file from this repo into your `~/.vim/after/ftplugin/markdown/` (creating directories as necessary), or follow your vim package manager's instructions, e.g. with vim-plug, add the following to your init.vim

`Plug 'twidxuga/vim-instant-markdown'`

- Ensure you have the line `filetype plugin on` in your `init.vim`
- Open a markdown file in vim and enjoy!

Configuration
-------------
### g:instant_markdown_slow

By default, vim-instant-markdown will update the display in realtime.  If that taxes your system too much, you can specify

```
let g:instant_markdown_slow = 1
```

before loading the plugin (for example place that in your `~/.config/nvim/init.vim`). This will cause vim-instant-markdown to only refresh on the following events:

- No keys have been pressed for a while
- A while after you leave insert mode
- You save the file being edited

### g:instant_markdown_autostart
By default, vim-instant-markdown will automatically launch the preview window when you open a markdown file. If you want to manually control this behavior, you can specify

```
let g:instant_markdown_autostart = 0
```

in your init.vim. You can then manually trigger preview via the command ```:InstantMarkdownPreview```. This command is only available inside markdown buffers and when the autostart option is turned off.

### g:instant_markdown_open_to_the_world
By default, the server only listens on localhost. To make the server available to others in your network, edit your init.vim and add

```
let g:instant_markdown_open_to_the_world = 1
```

Only use this setting on trusted networks!

### g:instant_markdown_allow_unsafe_content
By default, scripts are blocked. To allow scripts to run, edit your init.vim and add

```
let g:instant_markdown_allow_unsafe_content = 1
```

### g:instant_markdown_allow_external_content
By default, external resources such as images, stylesheets, frames and plugins are allowed.
To block such content, edit your init.vim and add

```
let g:instant_markdown_allow_external_content = 0
```

### g:instant_markdown_serve_folder_tree 
By defaul, instant-makrdown-d will serve files from the folder tree starting with the current markdown files working directory. This is useful for serving files/images that may be linked to in the markdown being edited.

To prevent this set this option to 0 in your init.vim: 

```
let g:instant_markdown_serve_folder_tree = 0
```

Supported Platforms
-------------------
Neovim running on Unix/Linuxes*

<sub>*: One annoyance in Linux is that there's no way to reliably open a browser page in the background, so you'll likely have to manually refocus your vim session everytime you open a Markdown file. If you have ideas on how to address this I'd love to know!</sub>

This fork of instant markdown was NOT tested on other platforms, thought it may just work. 
