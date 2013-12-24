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

doc:
	$(RUBBER) $(DOC).tex

view: viewpdf

print: pdf
	$(PRINT) $(DOC).pdf

pdf:
	$(RUBBER) $(DOC).tex

viewpdf: pdf
	$(ACROREAD) $(DOC).pdf

clean:
	rm -f *.aux $(DOC).{toc,out,lol,lof,pdf,log,idx,ilg,ind}
	rm -rf .AppleDouble

spell:
	$(SPELL) $(SPELLOPTS) -t $(DOC).tex

commit: clean
	$(VCS) commit .
	$(VCS) push origin master

# this needs testing
# it's a leftover from SVN days
# better to use texlive-latex-git-log-doc with git, I guess
#changelog: commit
#	$(VCS) update
#	$(VCS) log --xml | xsltproc -o changelog-tmp.tex svnlog.xslt -
#	echo "\chapter{Changelog}" > changelog.tex
#	cat changelog-tmp.tex >> changelog.tex
#	rm changelog-tmp.tex

update:
	$(VCS) update
