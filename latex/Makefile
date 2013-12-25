TEX = latex
DVIPS = dvips
XDVI = xdvi
PDF = pdflatex
RUBBER = rubber -m pdftex 
ACROREAD = okular
MAKEINDEX = makeindex
VCS = git
DOC = Developing-with-SailfishOS
PRINT = lpr -P epson-usb
SPELL = hunspell
SPELLOPTS = -d en_GB

all: pdf

view: viewpdf

print: pdf
	$(PRINT) $(DOC).pdf

pdf:
	$(RUBBER) $(DOC).tex

force: gitlog
	# without force it does not pick up that gitlog changed
	$(RUBBER) --force $(DOC).tex

viewpdf: pdf
	$(ACROREAD) $(DOC).pdf

clean:
	rm -f *.aux $(DOC).{toc,out,lol,lof,pdf,log,idx,ilg,ind,dvi}
	rm -rf gitlog.tex
	rm -rf .AppleDouble

spell:
	$(SPELL) $(SPELLOPTS) -t $(DOC).tex

commit: clean
	$(VCS) commit .
	$(VCS) push origin master

# use latex-git-log to create a changelog file
# not enabled by default as it's not perfect, esp at end of doc
gitlog:
	#latex-git-log --lang=en --width=14 > gitlog.tex
	latex-git-log --lang=en > gitlog.tex

pull:
	$(VCS) pull
