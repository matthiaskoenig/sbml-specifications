# File name   : Makefile
# Description : Makefile for sbml document
# Author(s)   : Michael Hucka <mhucka@cds.caltech.edu>
# Organization: CDS, Caltech
# Language    : Make
# Created     : 2000-10-17
# Revision    : Makefile,v 1.1.1.1 2002/12/05 23:59:38 mhucka Exp
# /cvsroot/sbw/sbw/project/docs/sbml/sbml-level-1/version-1/Makefile,v

BASENAME = sbml-level-1

default: dvi

dvi:;
	-@/bin/rm -f $(BASENAME).toc $(BASENAME).aux
	latex $(BASENAME).tex
	bibtex $(BASENAME)
	latex $(BASENAME).tex
	latex $(BASENAME).tex
	latex $(BASENAME).tex

pdf:;
	make eps
	-@/bin/rm -f $(BASENAME).toc $(BASENAME).aux
	pdflatex $(BASENAME).tex
	bibtex $(BASENAME)
	pdflatex $(BASENAME).tex
	pdflatex $(BASENAME).tex
	pdflatex $(BASENAME).tex
	pdflatex $(BASENAME).tex

eps:;
	@(for i in *.eps; do echo "converting $$i to PDF"; convert -density 600x600 $$i epdf:$${i/.eps/.pdf}; done)

html:;
	latex2html -white -split +0 -show_section_numbers -image_type gif \
		   -no_navigation -local_icons -discard \
		   -mkdir -dir html $(BASENAME)
