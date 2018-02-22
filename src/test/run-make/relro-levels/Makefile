-include ../tools.mk

# This tests the different -Crelro-level values, and makes sure that they they work properly.

all:
ifeq ($(UNAME),Linux)
	# Ensure that binaries built with the full relro level links them with both
	# RELRO and BIND_NOW for doing eager symbol resolving.
	$(RUSTC) -Crelro-level=full hello.rs
	readelf -l $(TMPDIR)/hello | grep -q GNU_RELRO
	readelf -d $(TMPDIR)/hello | grep -q BIND_NOW

	$(RUSTC) -Crelro-level=partial hello.rs
	readelf -l $(TMPDIR)/hello | grep -q GNU_RELRO
endif
