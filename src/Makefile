# Contributed by holomorph, 2013.
# Added to by Andres Raba, 2013-2015.

FIG := $(patsubst %.svg,%.pdf,$(wildcard fig/*/*.svg))

all: jsicp.pdf

jsicp.pdf: jsicp.tex exercises.tex figures.tex coverpage.pdf ${FIG}
	latexmk -pdflatex="xelatex %O %S" -pdf -dvi- -ps- $<

sicp.tex: sicp.texi preamble.tex postamble.tex 
	./texi-to-latex.pl $<

exercises.tex figures.tex: ex-fig-ref.pl
	./ex-fig-ref.pl -e > exercises.tex; \
	./ex-fig-ref.pl -f > figures.tex

%.pdf: %.svg
	inkscape $(abspath $<) --export-area-page --export-filename $(abspath $@)

clean:
	latexmk -CA

clean-all: clean
	${RM} ${FIG} sicp.tex exercises.tex figures.tex coverpage.pdf

.PHONY: all clean clean-all
