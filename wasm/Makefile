ifeq ($(OS),Windows_NT)
    BROWSER = start
else
	UNAME := $(shell uname -s)
	ifeq ($(UNAME), Linux)
		BROWSER = xdg-open
	endif
	ifeq ($(UNAME), Darwin)
		BROWSER = open
	endif
endif

.PHONY: all clean serve

all: wasm serve

demo: masquerade serve

wasm:
	GOOS=js GOARCH=wasm go build -o lib.wasm wasm.go

masquerade:
	GOOS=js GOARCH=wasm go build -o lib.wasm demo.go

serve:
	$(BROWSER) 'http://localhost:5000'
	serve

clean:
	rm -f *.wasm

debug:
	@echo $(UNAME)