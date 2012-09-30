[![Build Status](https://secure.travis-ci.org/rolandwalker/ido-load-library.png)](http://travis-ci.org/rolandwalker/ido-load-library)

Overview
========

Load-library alternative for Emacs using `ido-completing-read`.

Quickstart
----------

```lisp
(require 'ido-load-library)
 
;; execute M-x ido-load-library RET
```

ido-load-library
----------------

Ido-load-library is an alternative to `load-library` which uses
`ido-completing-read` for completion against all available
libraries in your `load-path`.

The interactive command `ido-load-library` is made available,
though not bound to any key.  It can be executed via

	M-x ido-load-library

or bound via something like

```lisp
(define-key global-map (kbd "C-c l") 'ido-load-library)
```

or safely aliased to `load-library`

```lisp
(defalias 'load-library 'ido-load-library)
```

ido-load-library-find
---------------------

The interactive command `ido-load-library-find` is also
available.  Like `ido-load-library`, it searches your
`load-path`, but instead of loading the selected library,
it visits the file in a buffer.

Bugs
----

When invalidating the disk cache, `ido-load-library` only checks
whether `load-path` has changed, not whether new files were added
to existing paths.  Workarounds:

1.  Install libraries using ELPA/package.el, in which case this
    assumption always works.
2.  Wait for the cache to expire (7 days).
3.  Give universal prefix argument to `ido-load-library`
    to force invalidation of the cache.

Compatibility and Requirements
------------------------------

	GNU Emacs version 24.3-devel     : yes, at the time of writing
	GNU Emacs version 24.1 & 24.2    : yes
	GNU Emacs version 23.3           : yes
	GNU Emacs version 22.3 and lower : no

Uses if present: [persistent-soft.el](http://github.com/rolandwalker/persistent-soft) (Recommended)
