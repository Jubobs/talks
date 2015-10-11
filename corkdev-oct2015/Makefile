# Unlisted dependencies:
#   * Some TeX distribution (e.g. TeX Live)
#   * gitdags v0.1
#	https://github.com/Jubobs/gitdags
#   * Image Magick
#	http://www.imagemagick.org/script/index.php
#   * pandoc v1.15.0.6
#	https://github.com/jgm/pandoc
#   * Slidy
#	http://www.w3.org/Talks/Tools/Slidy2

BASENAME  = slides
HEADER    = header.inc
LATEXMK   = pdflatex -shell-escape
RM        = rm -f
TEXSRC    = $(wildcard *.tex)

all: $(BASENAME).html
	open $(BASENAME).html

$(BASENAME).html: $(BASENAME).md \
			header.inc \
			Makefile \
			*.svg
	pandoc	--data-dir=. \
		--standalone \
		--to slidy \
		--css $(BASENAME).css \
		--highlight-style haddock \
		--include-in-header=$(HEADER) \
		-o $(BASENAME).html \
		$(BASENAME).md

%.svg: %.tex
	$(LATEXMK) $^

clean:
	$(RM) *.aux *.log *.out *.pdf

cleanall: clean
	$(RM) $(BASENAME).html *.svg

.PHONY: all clean cleanall
