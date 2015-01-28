#
# Generic LaTeX makefile
#
# * set TARGET to main filename
#

TARGET=rcv

# TeX programs
TEX=latex
LATEX=latex
BIBTEX=bibtex
DVIPS=dvips
PS2PDF=ps2pdf

# Use operating system-specific PDF viewer
UNAME := $(shell uname)

ifeq ($(UNAME), Linux)
EXT=ps
VIEWER=evince
endif

ifeq ($(UNAME), Darwin)
EXT=pdf
VIEWER=open
endif


%.dvi : %.tex
	$(LATEX) $<
	$(BIBTEX) $(subst tex,aux,$<)
	$(LATEX) $<
	$(LATEX) $<

%.ps : %.dvi
	$(DVIPS) -z $< -o $@

%.pdf : %.ps
	$(PS2PDF) $<

default: $(TARGET).$(EXT)
	$(VIEWER) $(TARGET).$(EXT)

clean:
	-rm -f $(TARGET).{aux,log,nav,out,snm,toc,vrb,bbl}
	-rm -f ./*~

clobber: clean
	-rm -f ./*.{pdf,dvi,ps}
