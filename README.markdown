Overview
=========
Special treatment for namespace prefixes in Emacs hippie-expand.

hippie-namespace
----------------
Enabling the minor mode adds a limited number of very common
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

	(define-key global-map (kbd "M-/") 'hippie-expand)

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
Tested on GNU Emacs versions 23.3 and 24.1

No external dependencies
