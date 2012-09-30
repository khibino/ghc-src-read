
%.pdf: %.dvi
	dvipdfmx $(@:.pdf=.dvi)

%.dvi %.log %.aux: %.tex
	platex $<

# %.png: %.dia
# 	dia -e $@ $<

%.ppm: %.png
	convert $< $@

%.bb: %.ppm
	bbox $< > $@

%.simpl: %.hs
	ghc -c -ddump-simpl $< > $@

%.o: %.hs
	ghc -c -Wall $<

images = \
	HscPipe2.png HscPipe2.bb



all:: $(images) Foo.simpl GhcSimplGVN.dvi GhcSimplGVN.pdf

clean::
	$(RM) *.o *.hi
	$(RM) *.dvi *.log *.aux *.toc
	$(RM) *.vrb *.out *.nav *.snm
	$(RM) *.bb

veryclean: clean
	$(RM) *.pdf
