# beancount.el: Emacs editor support for [beancount](http://furius.ca/beancount)

## Explanation

This package is forked from
https://bitbucket.org/blais/beancount/src/default/editors/emacs/beancount.el .

And made the following change:

- Read the account names from the specified accounts files and provide it to the
  autocomplete function.

## Installation Examples

### doom-emacs

```emacs-lisp
;; packages.el
(package! beancount
  :recipe (:host github :repo "cnsunyour/beancount.el"))

;; config.el
(use-package! beancount
  :defer t
  :bind
  ("C-M-b" . (lambda ()
               (interactive)
               (find-file "~/Dropbox/beancount/main.bean")))
  :mode
  ("\\.bean\\(?:count\\)?\\'" . beancount-mode)
  :config
  (setq beancount-accounts-files
        (directory-files "~/Dropbox/beancount/accounts/"
                         'full
                         (rx ".bean" eos))))
```

### Straight

```emacs-lisp
(use-package beancount
  :straight (beancount
             :type git
             :host github
             :repo "cnsunyour/beancount.el")
  :bind
  ("C-M-b" . (lambda ()
               (interactive)
               (find-file "~/Dropbox/beancount/main.bean")))
  :mode
  ("\\.bean\\(?:count\\)?\\'" . beancount-mode)
  :config
  (setq beancount-accounts-files
        (directory-files "~/Dropbox/beancount/accounts/"
                         'full
                         (rx ".bean" eos))))
```

## License

This code is distributed under the [GNU General Public License](COPYING);
