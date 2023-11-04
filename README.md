# chforbid

**chforbid** is a utility script to ensure you don't make use of forbidden
functions in your 42 projects.

In order to install it, clone the repository and execute:
```sh
pip install tree_sitter
git clone https://github.com/tree-sitter/tree-sitter-c vendor/tree-sitter-c
```

You can then run it:
```
% ./chforbid 
usage: chforbid [-h] [-a ALLOWED_FUNCTIONS] filename [filename ...]
```

My personal workflow is to have additional Makefile rules in a separate file
I don't commit, such as *myrules.mk*, which runs *chforbid*:
```make
all: norm chforbid tests

ALLOWED_FUNCTIONS = malloc free

chforbid:
	@chforbid -a "$(ALLOWED_FUNCTIONS)" *.c

.PHONY: chforbid
```
