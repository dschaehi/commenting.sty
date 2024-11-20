---
author: Jae Hee Lee
date: 2024-11-20
title: LaTeX Commenting Package
---

# Description

A LaTeX package for collaborative academic writing with sophisticated
comment management and tracking features. Designed with accessibility in
mind, featuring colorblind-safe colors for better collaboration.

# Features

-   Color-coded inline comments with author attribution
-   Distinct footnote-style annotations
-   Tracked text additions with author identification
-   Author-specific colored environments
-   Smart draft/final mode switching
-   Colorblind-safe predefined colors

# Installation

1.  Place `commenting.sty`{.verbatim} in your LaTeX project directory or
    in your local texmf tree

2.  Add the package to your document:

    ``` latex
    \usepackage[draft|final]{commenting}
    ```

# Usage

## Author Registration

Register authors with their assigned colors:

``` latex
\registerauthor{alice}{cbBlue}    % Register Alice with blue color
\registerauthor{bob}{cbOrange}    % Register Bob with orange color
```

## Available Commands

Each registered author gets access to these commands:

  Command                                Description
  -------------------------------------- ----------------------------
  `\<author>inline{text}`{.verbatim}     Add an inline comment
  `\<author>footnote{text}`{.verbatim}   Add a footnote comment
  `\<author>add{text}`{.verbatim}        Add tracked text changes
  `\begin{<author>env}...`{.verbatim}    Create colored environment

## Example Usage

``` latex
This is a \aliceinline{needs clarification} paragraph.
Here's a statement\bobfootnote{Add citation}.
This is \aliceadd{very} important.

\begin{bobenv}
This entire paragraph needs revision.
\end{bobenv}
```

# Color Documentation

Available colorblind-safe colors:

  Color Name   Description    RGB Values      Usage
  ------------ -------------- --------------- ---------------------
  cbBlue       Strong blue    (51,114,189)    Primary emphasis
  cbOrange     Vivid orange   (255,127,42)    Secondary emphasis
  cbTeal       Bright teal    (64,204,204)    Tertiary emphasis
  cbRed        Clear red      (217,37,37)     Important notes
  cbPurple     Muted purple   (148,103,189)   Additional comments

# Package Options

Two modes available:

``` latex
\usepackage[draft]{commenting}  % Show all comments (default)
\usepackage[final]{commenting} % Hide all comments
```

# Author Information

Author: Jae Hee Lee Website: [jaeheelee.de](http://jaeheelee.de)
Version: 2024/11/20 v1.1

# License

This package is distributed under the LaTeX Project Public License
(LPPL).
