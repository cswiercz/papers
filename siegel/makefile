#
# Generic LaTeX makefile
#
# * set TARGET to main filename
#

TARGET=siegel

# TeX programs
TEX=latex
LATEX=latex
DVIPS=dvips
DVIPDF=dvipdf

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

%.ps : %.dvi
	$(DVIPS) $<

%.pdf : %.dvi
	$(DVIPDF) $<

default: $(TARGET).$(EXT)
	$(VIEWER) $(TARGET).$(EXT)

clean:
	-rm -f $(TARGET).{aux,log,nav,out,snm,toc,vrb}
	-rm -f ./*~

clobber: clean
	-rm -f ./*.{pdf,dvi,ps}