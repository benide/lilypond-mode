This repo contains the Emacs `lilypond-mode` files from version 2.22.2 of Lilypond. `lilypond-words.el` is generated from the Nix `lilypond-with-fonts` package.

I'm putting this repo here because I was getting annoyed with trying to figure out how to use this easily with Elpaca. The bad option was:

```elisp
(elpaca-use-package
  (lilypond-mode :type git
	             :host nil
	             :repo "https://git.savannah.gnu.org/git/lilypond.git"
	             :files ("elisp/*.el")
                 :pre-build ("python" "scripts/build/lilypond-words.py" "--el" "--dir=elisp/"))
  :mode ("\\.ly$" . LilyPond-mode)
  :commands (LilyPond-mode))
```

but now I can instead do:

```elisp
(elpaca-use-package
  (lilypond-mode :type git
	             :host github
	             :repo "benide/lilypond-mode"
                 :files ("*.el"))
  :mode ("\\.ly$" . LilyPond-mode)
  :commands (LilyPond-mode))

```

The latter doesn't need to clone the entire Lilypond repo and doesn't need to use python to create `lilypond-words.el`.

