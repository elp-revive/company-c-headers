[![License: GPL v2](https://img.shields.io/badge/License-GPL%20v2-blue.svg)](https://www.gnu.org/licenses/gpl-2.0)
[![JCS-ELPA](https://raw.githubusercontent.com/jcs-emacs/badges/master/elpa/v/company-c-headers.svg)](https://jcs-emacs.github.io/jcs-elpa/#/company-c-headers)

# company-c-headers
> Auto-completion for C/C++ headers using Company

[![CI](https://github.com/elp-revive/company-c-headers/actions/workflows/test.yml/badge.svg)](https://github.com/elp-revive/company-c-headers/actions/workflows/test.yml)

This library enables the completion of C/C++ header file names using [company-mode](https://company-mode.github.io) for Emacs.

![](screenshot.png)

When you type an `#include` declaration within a supported major mode (currently
`c-mode`, `c++-mode` and `objc-mode`), company-c-headers will search for completion
candidates within the defined include paths. There are “system” and “user” include
paths, for `#include <...>` and `#include "..."` declarations, respectively.

During completion, the path to the current candidate can be seen in the minibuffer,
such as in the screenshot above. Also during completion, you can use `C-w` to
temporarily display the currently-selected header file.

This library is inspired by [auto-complete-c-headers](https://github.com/mooz/auto-complete-c-headers).

## Installation

The best way to install this package is via [MELPA](https://melpa.org/#/).

## Setup

With the company-c-headers library added to the `load-path`, all you need to do
to initialize it is:

Alternatively, you can bind the `company-c-headers-path-system` and
`company-c-headers-path-user` variables to functions which return the corresponding
paths. For example, if you are using [EDE](http://cedet.sourceforge.net/ede.shtml),
you can use the following:

```elisp
(defun ede-object-system-include-path ()
  "Return the system include path for the current buffer."
  (when ede-object
    (ede-system-include-path ede-object)))

(setq company-c-headers-path-system 'ede-object-system-include-path)
```
