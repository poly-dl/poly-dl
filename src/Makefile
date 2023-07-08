
all: build run

build:
	dune build main/prototype.exe

run:
	dune exec ./main/prototype.exe

clean:
	dune clean
	rm -f ../docs/typechecker.js

libjs:
	dune build --profile release main/lib_js.bc.js
	cp _build/default/main/lib_js.bc.js ../docs/typechecker.js
	chmod +w ../docs/typechecker.js

test:
	dune runtest
