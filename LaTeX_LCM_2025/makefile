PANDOC:=/usr/bin/pandoc
DEPENDENCIES= dependencies
PYTHON:=/usr/bin/python3
MDOPTS= --standalone\
		--from markdown+raw_html+tex_math_dollars\
		-t revealjs\
		-V revealjs-url=${DEPENDENCIES}/revealjs\
		-V theme=night\
		--no-highlight\
		--toc --toc-depth 1\
		--number-sections\
		--css=style.css\
		

# -V slideNumber=true\ -markdown_in_html_blocks
# --highlight-style=zenburn\ --mathml
.PHONY: all http

all: parte_1.html parte_2.html

%.html: %.md style.css template.html ${DEPENDENCIES}/revealjs
	$(PANDOC) $(MDOPTS) -o $@ $<

dependencies/revealjs:
	mkdir -p $(DEPENDENCIES)
	wget https://github.com/hakimel/reveal.js/archive/master.tar.gz
	tar xzvf master.tar.gz
	mv reveal.js-master/ ${DEPENDENCIES}/revealjs
	rm master.tar.gz

http:
	$(PYTHON) -m http.server