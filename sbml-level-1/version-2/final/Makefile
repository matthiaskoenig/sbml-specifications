# File name   : Makefile
# Description : Makefile for sbml document
# Author(s)   : Michael Hucka <mhucka@cds.caltech.edu>
# Organization: CDS, Caltech
# Language    : Make
# Created     : 2000-10-17
# Revision    : $Revision$
# $Id$

BASENAME = sbml-level-1
HTML_DIR = html

.PHONY: dvi pdf ps pdffigs html

default: dvi

dvi:;
	-@/bin/rm -f $(BASENAME).toc $(BASENAME).aux
	latex $(BASENAME).tex
	-bibtex $(BASENAME)
	latex $(BASENAME).tex
	latex $(BASENAME).tex
	latex $(BASENAME).tex

ps: dvi
	dvips -o $(BASENAME).ps $(BASENAME)

pdf: pdffigs
	-@/bin/rm -f $(BASENAME).toc $(BASENAME).aux
	pdflatex $(BASENAME).tex
	-bibtex $(BASENAME)
	pdflatex $(BASENAME).tex
	pdflatex $(BASENAME).tex
	pdflatex $(BASENAME).tex
	pdflatex $(BASENAME).tex

pdffigs:;
	(for i in figs/*.eps; do epstopdf $$i; echo $$i; done)

cekarticle.perl:
	ln -s ../../../../../sbw-cvs/project/tex/cekarticle.perl

html: cekarticle.perl
	/bin/rm -rf $(HTML_DIR)
	/bin/mkdir $(HTML_DIR)
	latex2html -white -split +0 -show_section_numbers -image_type gif \
		   -no_navigation -local_icons -discard \
		   -mkdir -dir $(HTML_DIR) $(BASENAME)
