FIXME = ../../../../Inst4CIM-KG/rdf-improved
JSON  = $(wildcard ../CIMJSON-LD/*.jsonld)
TRIG  = $(patsubst ../CIMJSON-LD/%.jsonld,%.trig, $(JSON))

all: $(TRIG)

echo:
	@echo $(TRIG)

%.trig: ../CIMJSON-LD/%.jsonld
	riot.bat --syntax jsonld --formatted trig $^ > temp.trig
	update.bat --update=$(FIXME)/fix-datatypes-and-model.ru --data=temp.trig --dump > $@
	rm temp.trig

# Important: Telemark-120-WattApp-GL is only available in GEOJSON not JSON-LD. So the trig file is made by hand, not with the above
