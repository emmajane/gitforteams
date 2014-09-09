# Produce PDFs from all Markdown files in a directory
# Lincoln Mullen | http://lincolnmullen.com | lincoln@lincolnmullen.com
# This makefile assumes pandoc is installed and configured. It doesn't
# check first.
#
# Installing and Configuring Pandoc
# The official Pandoc web site is: http://johnmacfarlane.net/pandoc/
#
# Installing the Necessary Software
# $ brew install haskell-platform
# $ xcode-select --install
# $ brew install gmp
# $ cabal update
# $ cabal install pandoc
# $ wget http://mirror.ctan.org/systems/mac/mactex/mactex-basic.pkg
#
# Add cabal and texbin to your path (~/.bashrc): export PATH=$PATH:$HOME/.cabal/bin:/usr/texbin
#
# Create a single PDF out of all known files. Must update the makefile.
# Opted to not use recursion because I didn't actually want all README
# files from the cookbooks
FILES := 01-intro/README.md	02-getting-started/README.md 03-clone-remote/README.md 04-config/README.md 05-init-local/README.md 06-connect-remote/README.md 07-branches/README.md 08-tags/README.md 09-find-and-fix/README.md 10-rollback-reset/README.md 11-rebase/README.md 12-github/README.md 13-bitbucket/README.md

once :
	pandoc $(FILES) -o README.pdf

# List files to be made by finding all *.md files and appending .pdf
# Only the looks in the current directory
PDFS := $(patsubst %.md,%.md.pdf,$(wildcard *.md))
 
# The all rule makes all the PDF files listed as separate PDFs.
# Only looks in the current directory
all : $(PDFS)

# This generic rule accepts PDF targets with corresponding Markdown 
# source, and makes them using pandoc
%.md.pdf : %.md
	pandoc $< -o $@
 
# Remove all PDF outputs
clean :
	rm $(PDFS)
 
# Remove all PDF outputs then build them again
rebuild : clean all
