# vim-yardoc

This plugin provides Ruby syntax extensions for highlighting [YARD documentation](https://github.com/lsegal/yard).
In contrast with [vim-yard](https://github.com/postmodern/vim-yard), vim-yardoc
piggy backs on Vim's existing Ruby syntax to provide an integrated experience.

## Contents

1. [Installation](#installation)
2. [Usage](#usage)
  - [Customization](#customization)
  - [Syntax groups](#syntax-groups)
3. [Contributing](#contributing)

## Installation

Assuming this isn't your first rodeo there are three approaches to installing
vim-yardoc.

- [With pathogen](#with-pathogen)
- [Without pathogen](#without-pathogen)
- [By hand](#by-hand)

### With pathogen

If you're not already using Tim Pope's fantastic [pathogen](https://github.com/tpope/vim-pathogen)
plugin, I would highly encourage you to do so. If you are, you're probably not
even reading this. However, in the event you are reading this, the instructions
are as follows:

```shell
% cd ~/.vim/bundle
% git clone https://github.com/noprompt/vim-yardoc.git
```

### Without pathogen

Install the [pathogen](https://github.com/tpope/vim-pathogen) plugin. See
[these](#with-pathogen) instructions.

### By hand

Clone this repo to a location on your computer.

```shell
% git clone https://github.com/noprompt/vim-yardoc.git /somewhere/vim-yardoc
```

Next, check to make sure you don't already have a `ruby.vim` file in
`~/.vim/after/syntax` like so:

```shell
% test -f ~/.vim/syntax/after/ruby.vim
% echo $?
```

If `1` is printed, you're good to copy the file:

```shell
% cp vim-yard/after/syntax/ruby.vim ~/.vim/syntax/after/ruby.vim
````

If `0` is printed, you can copy the contents of
`vim-yardoc/after/syntax/ruby.vim` to your existing Ruby syntax extensions
file:

```shell
% echo -e "\n\" BEGIN vim-yardoc {{{" >> ~/.vim/syntax/after/ruby.vim
% cat vim-yardoc/after/syntax/ruby.vim >> ~/.vim/syntax/after/ruby.vim
% echo -e "\n\" END vim-yardoc }}}" >> ~/.vim/syntax/after/ruby.vim
```

You do not need to run the first and last commands, however, it may serve as a
helpful marker in the future should you choose to edit the file again.

## Usage

This "plugin" merely provides extensions to Vim's Ruby syntax and changes almost
nothing in terms of the appearence of your Ruby documents. With the exception of
YARD [tags](http://rubydoc.info/docs/yard/file/docs/Tags.md#Tag_List) and
[directives](http://rubydoc.info/docs/yard/file/docs/Tags.md#Directive_List)
, which are linked to `rubyTodo`, all yard related syntax groups are linked to
`Comment`. You may find yourself somewhat underwhelmed after installing it. This
is intentional but, fear not, there are two good reasons for this posture.

The first reason is the desire to avoid making assumptions about which syntax
groups should link to others. Since viturally nothing can be known about your
particular configuration, except you're likely to have a Ruby syntax file in
your `$VIMRUNTIME` directory, highlight links are only made against `Comment`
and `rubyTodo` (as noted above).

The second reason, in tandem with the first, is the desire to leave
customization entirely up to you. This might be a bit off-putting for some but
having the flexibility to customize an experience you enjoy is certainly more
valuable than forcing you to customize one you do not. In some cases "sensible
defaults" simply do not exist.

### Customization

You can add your own custom highlight links to either your `.vimrc` file or to
your current theme. For instance, you might like YARD tags to look like to look
like instance variables (since both begin with an `@` symbol):

```viml
hi link yardGenericTag rubyInstanceVariable
```

It's really quite painless.

### Syntax groups

The following syntax groups are available for customization:

#### Tags (as listed [here](http://rubydoc.info/docs/yard/file/docs/Tags.md#Tag_List))
```
yardGenericTag
yardAbstract
yardApi
yardAttr
yardAttrReader
yardAttrWriter
yardAuthor
yardDeprecated
yardExample
yardNote
yardOption
yardOverload
yardParam
yardPrivate
yardRaise
yardReturn
yardSee
yardSince
yardTodo
yardVersion
yardYield
yardYieldParam
yardYieldReturn
```

#### Directives (as listed [here](http://rubydoc.info/docs/yard/file/docs/Tags.md#Directive_List))

```
yardGenericDirective
yardAttribute
yardEndGroup
yardGroup
yardMacro
yardMethod
yardParse
yardScope
yardVisibility
```

#### Types, Lists, and Hashes (as specified [here](http://rubydoc.info/docs/yard/file/docs/Tags.md#Hashes))

```
yardDuckType
yardType
yardLiteral
yardOrderDependentList
yardParametricType
yardTypeList
yardHashAngle
yardHashCurly
```

#### Delimiters

```
yardComma
yardArrow
```

## Contributing

Contributions and feedback are almost certainly encouraged. This is my first
shot at writing syntax extensions for Vim so any assistence or suggestion is
happily welcomed.
