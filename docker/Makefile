.PHONY: base quagga frr sdn

base:
	cd base && docker build -t andreymgn/base .

quagga: base
	cd quagga && docker build -t andreymgn/quagga .

frr: base
	cd frr && docker build -t andreymgn/frr .

sdn: base
	cd sdn && docker build -t andreymgn/sdn .
