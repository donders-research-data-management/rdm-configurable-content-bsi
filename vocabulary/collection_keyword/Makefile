VOC_CATEGORY = $(shell basename $(CURDIR))

VOCABULARIES = MeSH2015 SFN2013 

.PHONY: all $(VOCABULARIES)

all: $(VOCABULARIES)

$(VOCABULARIES):
	@echo "[$(VOC_CATEGORY)] building JSON document for vocabulary $@ ..."
	@python $(shell pwd)/utility/csv2json.py $@ $@.csv $@.json

clean:
	@echo "[$(VOC_CATEGORY)] removing index JSON files (i.e. *.json) ..."
	@rm -f *.json
