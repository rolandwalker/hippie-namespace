[![Build Status](https://secure.travis-ci.org/rolandwalker/hippie-namespace.png?branch=master)](http://travis-ci.org/rolandwalker/hippie-namespace)

Overview
========

Special treatment for namespace prefixes in Emacs hippie-expand.

Quickstart
----------

```elisp
(require 'hippie-namespace)
 
(global-hippie-namespace-mode 1)
 
(define-key global-map (kbd "M-/") 'hippie-expand)
 
;; type hi [M-/]     ; The first one or two letters of a namespace
                     ; found in the current buffer, followed by the
                     ; key bound to `hippie-expand'.
```

Explanation
-----------

The purpose of hippie-namespace is to save typing.

Enabling this minor mode adds a limited number of very common
prefixes to the `hippie-expand` expansion list.  These prefixes
(deduced from buffer content) will be the first completions
considered.

Furthermore, hippie-namespace completions are treated specially:
when `hippie-expand` proposes a namespace completion, it will not
cycle.  Instead, the namespace completion is implicitly accepted,
and further invocations of `hippie-expand` will build on the
expansion.

For example, the common prefix of all symbols in this library is
"hippie-namespace-".  If, while editing this library, the user
types "hi [hippie-expand]" or even just "h [hippie-expand]",
the full prefix is expanded.

"hi [hippie-expand] [hippie-expand] ..." will then cycle through
all completions which match the prefix.

This mode makes more sense for some languages and less sense for
others.  In most languages, the declared "namespace" is
infrequently used in its own context.  (For Emacs Lisp that is
not the case.)

Note that you should also have `hippie-expand` bound to a key.
Many people override dabbrev expansion:

```elisp
(define-key global-map (kbd "M-/") 'hippie-expand)
```

Determining Namespaces
----------------------

The minor mode will examine each buffer to guess namespace prefixes
dynamically.  If the guess is not good enough, you may add to the
list by executing

	M-x hippie-namespace-add

or by adding a file-local variable at the end of your file:

```elisp
;; Local Variables:
;; hippie-namespace-local-list: (namespace-1 namespace-2)
;; End:
```

Mode-specific namespace finders are easy to write.  Search for "Howto"
in the source.

Notes
-----

Integrates with [expand-region](http://github.com/magnars/expand-region.el), adding an expansion which is aware of the
namespace and non-namespace portions of a symbol.

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

	GNU Emacs version 24.4-devel     : yes, at the time of writing
	GNU Emacs version 24.3           : yes
	GNU Emacs version 23.3           : yes
	GNU Emacs version 22.2           : yes, with some limitations
	GNU Emacs version 21.x and lower : unknown

Uses if present: [expand-region](http://github.com/magnars/expand-region.el)
