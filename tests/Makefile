LIB_TESTS = 00_library.libtest

TXT_TESTS = 01_text.txttest

BIN = main

CFLAGS = -I . \
		 -I ../ \
		 -I ../include

CC = gcc

%.libtest: %.expect %.c
	@echo Test: $*...
	@eval $(CC) $(CFLAGS) $*.c -o $*.o
	@eval ./$*.o 2>&1 >$*.output
	@if [ "x`diff -qbu $*.expect $*.output`" != "x" ]; \
	then \
        	echo "Test $* FAILED"; \
        	diff -u $*.expect $*.output; \
       		rm -f $*.output $*.o; \
		exit 1; \
	fi; \
       	rm -f $*.output $*.o

%.txttest: %.expect %.input
	@echo Test: $*...
	@echo `cat $*.input >../$(BIN)` 2>&1 >$*.output
	@if [ "x`diff -qbu $*.expect $*.output`" != "x" ]; \
	then \
        	echo "Test $* FAILED"; \
        	diff -u $*.expect $*.output; \
       		rm -f $*.output; \
		exit 1; \
	fi; \
       	rm -f $*.o $*.output
	
all: libtest txttest

libtest: $(LIB_TESTS)
txttest: $(TXT_TESTS)
	@echo "All tests passed!"

