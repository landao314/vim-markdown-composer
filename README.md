# vim-markdown-composer

[![Build Status](https://travis-ci.org/euclio/vim-markdown-composer.svg)](https://travis-ci.org/euclio/vim-markdown-composer)

vim-markdown-composer is a plugin that adds asynchronous markdown preview to
[Neovim] and [vim].

![](https://i.imgur.com/ZtyjjRD.gif)

## Requirements

This plugin supports Windows, macOS, and Linux.

In addition to vim or Neovim, vim-markdown-composer requires a distribution of
[Rust] with `cargo`. To easily install the lastest version of Rust with `cargo`,
check out [rustup.rs](https://www.rustup.rs/).

vim-markdown-composer officially targets the latest version of [stable Rust].

## Installation

Use whatever plugin manager you like. If you aren't familiar with plugin
managers, I recommend [vim-plug].

Here's an an example of managing installation with vim-plug:

```vim
function! BuildComposer(info)
  if a:info.status != 'unchanged' || a:info.force
    if has('nvim')
      !cargo build --release
    else
      !cargo build --release --no-default-features --features json-rpc
    endif
  endif
endfunction

Plug 'euclio/vim-markdown-composer', { 'do': function('BuildComposer') }
```

You should run `cargo build --release` in the plugin directory after
installation. Vim support requires the `json-rpc` cargo feature.

If you use the above snippet, everything should be taken care of automatically.

## Documentation

`:help markdown-composer`, or check out the `doc` directory.

# Acknowledgments

This plugin is inspired by suan's [vim-instant-markdown].

This plugin was built with [aurelius], a Rust library for live-updating markdown
previews.

[Rust]: http://www.rust-lang.org/
[cargo]: https://crates.io/
[Neovim]: http://neovim.io/
[vim]: http://www.vim.org
[vim-instant-markdown]: https://github.com/suan/vim-instant-markdown
[Neovim remote plugin]: http://neovim.io/doc/user/remote_plugin.html
[vim-plug]: https://github.com/junegunn/vim-plug
[msgpack-rpc]: https://github.com/msgpack-rpc/msgpack-rpc
[aurelius]: https://github.com/euclio/aurelius
[stable Rust]: https://www.rust-lang.org/downloads.html
