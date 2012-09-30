[![Build Status](https://secure.travis-ci.org/rolandwalker/hippie-namespace.png)](http://travis-ci.org/rolandwalker/hippie-namespace)

Overview
========

Special treatment for namespace prefixes in Emacs hippie-expand.

Quickstart
----------

```lisp
(require 'hippie-namespace)
 
(global-hippie-namespace-mode 1)
 
(define-key global-map (kbd "M-/") 'hippie-expand)
 
;; type hi [M-/]     ; The first one or two letters of a namespace
                     ; found in the current buffer, followed by the
                     ; key bound to `hippie-expand'.
```

hippie-namespace
----------------

Enabling this minor mode adds a limited number of very common
prefixes to the hippie-expand expansion list.  These prefixes
(deduced from buffer content) will be the first completions
considered.

Furthermore, namespace completions are treated specially: when
hippie-expand proposes a namespace completion, it does not cycle.
Instead, the completion is immediately accepted, and further
invocations of hippie-expand build from the expanded text.

For example, the common prefix of all symbols in this library is
"hippie-namespace-".  If the user types "hi [hippie-expand]" or
even just "h [hippie-expand]", the full prefix is expanded.

"hi [hippie-expand] [hippie-expand]" will start cycling through the
completions which match the prefix.

This mode makes more sense for some languages and less sense for
others.  In most languages, the declared "namespace" is
infrequently used in its own context.  (For Emacs Lisp that is
not the case.)

Note that you should also have hippie-expand bound to a key.
Many people override dabbrev expansion:

```lisp
(define-key global-map (kbd "M-/") 'hippie-expand)
```

Notes
-----

Integrates with `expand-region`, adding an expansion which is aware of the
namespace and non-namespace portions of a symbol.

Mode-specific namespace finders are easy to add.  Search for "Howto" in the
source.

See Also
--------

M-x customize-group RET hippie-namespace RET
M-x customize-group RET hippie-expand RET

Bugs
----

Breaks using C-u [hippie-expand] to undo. Workaround: use
regular undo commands.

Compatibility and Requirements
------------------------------

	GNU Emacs version 24.3-devel     : yes, at the time of writing
	GNU Emacs version 24.1 & 24.2    : yes
	GNU Emacs version 23.3           : yes
	GNU Emacs version 22.3 and lower : no

No external dependencies
