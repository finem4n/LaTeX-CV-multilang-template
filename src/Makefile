FILENAME = "main"
FIRSTNAME = "First"
LASTNAME = "Last"
## Your favourite pdf viewer, e.g. okular
PDFVIEWER = zathura

## -----------------------------------------
##       DO NOT EDIT BELOW THIS LINE
## -----------------------------------------

## Fork of:
## Makefile von Karl Voit (Karl@Voit.net)
## fuer LaTeX-Vorlagen nach Dinopolis
## Fork by finem4n made for polish folks or Englishmen in -N-e-w-Y-o-r-k- Warsaw

## (urspruengliche Fassung: Harald Krottmaier)

## some Makefile-hints taken from: 
## http://www.ctan.org/tex-archive/help/uk-tex-faq/Makefile

BUILD_DIR := build
OUT_DIR := ../output

## COMMANDS:
PDFLATEX_CMD = pdflatex -output-directory ${BUILD_DIR}
## TIMESTAMP = `/bin/date +%Y-%m-%d`
## PL_TIMESTAMP_AND_PROJECT = ${TIMESTAMP}_${FIRSTNAME}_${LASTNAME}_-_Lebenslauf_deutsch.pdf
## EN_TIMESTAMP_AND_PROJECT = ${TIMESTAMP}_${FIRSTNAME}_${LASTNAME}_-_CV_english.pdf
PL_PROJECT = ${FIRSTNAME}_${LASTNAME}-cv_pl.pdf
EN_PROJECT = ${FIRSTNAME}_${LASTNAME}-cv_en.pdf

#help
#helpThe main targets of this Makefile are:
#help	help	this help
.PHONY: help
help:
	@sed -n 's/^#help//p' < Makefile

#help	all	makes the polish version and the english version
.PHONY: all
all: pdfen pdfpl

#help	pdfen	makes the english pdf-file
.PHONY: pdfen
pdfen: clean
	-rm -r ${OUT_DIR}/*cv_en.pdf language.tex
	@mkdir -p ${BUILD_DIR}
	@mkdir -p ${OUT_DIR}
	ln -s i18n/en.tex language.tex
	${PDFLATEX_CMD} ${FILENAME}
	${PDFLATEX_CMD} ${FILENAME}
	-mv ${BUILD_DIR}/${FILENAME}.pdf ${OUT_DIR}/${EN_PROJECT}

#help	pdfpl	makes the polish pdf-file
.PHONY: pdfpl
pdfpl: clean
	-rm -r ${OUT_DIR}/*cv_pl.pdf language.tex
	@mkdir -p ${BUILD_DIR}
	@mkdir -p ${OUT_DIR}
	ln -s i18n/pl.tex language.tex
	${PDFLATEX_CMD} ${FILENAME}
	${PDFLATEX_CMD} ${FILENAME}
	-mv ${BUILD_DIR}/${FILENAME}.pdf ${OUT_DIR}/${PL_PROJECT}

# --------------------------------------------------------

#help	view	open PDF files in reader
.PHONY: view
view:
	${PDFVIEWER} ${OUT_DIR}/*.pdf

#help	clean	clean up temporary files
.PHONY: clean
clean:
	-rm -r ${BUILD_DIR} language.tex -f

#help	force	force rebuild next run
.PHONY: force
force:
	touch *tex

# TOOLS:

#help	zip	create ZIP-file only of the two PDF-files(!)
.PHONY: zip
zip: clean all
	-rm cv.zip
	zip cv.zip *_${FIRSTNAME}_${LASTNAME}_-_Lebenslauf_deutsch.pdf *_${FIRSTNAME}_${LASTNAME}_-_CV_english.pdf
	unzip -l cv.zip

#end
