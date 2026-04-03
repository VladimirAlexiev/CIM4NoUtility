FIXME = ../../../../Inst4CIM-KG/
JSON  = $(wildcard ../CIMJSON-LD/*.jsonld)
TRIG = $(patsubst ../CIMJSON-LD/%.jsonld,%.trig, $(JSON)) Telemark-120_AO.trig

all: $(TRIG)

echo:
	@echo $(TRIG)

%.trig: ../CIMJSON-LD/%.jsonld
	riot.bat --syntax jsonld --formatted trig $^ > temp.trig
	update.bat --update=$(FIXME)/rdf-improved/fix-datatypes-and-model.ru --data=temp.trig --dump > $@
	rm temp.trig

Telemark-120_AO.trig: ../CIMJSON-LD/AviationObstacle/Telemark-120_AO.jsonld
	perl $(FIXME)/rdfs-improved/fix-namespaces.pl $^ | riot.bat --syntax jsonld --formatted trig > temp.trig
	update.bat --update=$(FIXME)/rdf-improved/fix-datatypes-and-model.ru --data=temp.trig --dump > $@
	rm temp.trig
