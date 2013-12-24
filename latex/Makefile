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

pdf: vc.tex
	$(RUBBER) $(DOC).tex

viewpdf: pdf
	$(ACROREAD) $(DOC).pdf

clean:
	rm -f *.aux $(DOC).{toc,out,lol,lof,pdf,log,idx,ilg,ind}
	rm -rf vc.tex
	rm -rf .AppleDouble

spell:
	$(SPELL) $(SPELLOPTS) -t $(DOC).tex

commit: clean
	$(VCS) commit .
	$(VCS) push origin master

# use latex-git-log to create a changelog file
vc.tex:
	latex-git-log --lang=en > vc.tex

pull:
	$(VCS) pull
