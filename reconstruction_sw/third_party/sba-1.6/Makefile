#
# Makefile for Sparse Bundle Adjustment library & demo program
#
CC=gcc
#ARCHFLAGS=-march=pentium4 # YOU MIGHT WANT TO UNCOMMENT THIS FOR P4
CFLAGS=$(ARCHFLAGS) -O3 -funroll-loops -Wall #-Wstrict-aliasing #-g -pg
OBJS=sba_levmar.o sba_levmar_wrap.o sba_lapack.o sba_crsm.o sba_chkjac.o
SRCS=sba_levmar.c sba_levmar_wrap.c sba_lapack.c sba_crsm.c sba_chkjac.c
MAKE=make

all: libsba.so

libsba.so: 
	$(CC) -fPIC -c sba.h sba_levmar.c sba_levmar_wrap.c sba_lapack.c sba_crsm.c sba_chkjac.c
	$(CC) -shared -o libsba.so $(OBJS) -llapack -lblas

sba_levmar.o: sba.h sba_chkjac.h compiler.h
sba_levmar_wrap.o: sba.h
sba_lapack.o: sba.h compiler.h
sba_crsm.o: sba.h
sba_chkjac.o: sba.h sba_chkjac.h compiler.h

clean:
	@rm -f $(OBJS)
	rm libsba.so

depend:
	makedepend -f Makefile $(SRCS)

# DO NOT DELETE THIS LINE -- make depend depends on it.
