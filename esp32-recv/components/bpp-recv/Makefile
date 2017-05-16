#Makefile for a host build of the receiver.

OBJS=main.o chksign_mbedtls.o defec.o serdec.o hexdump.o subtitle.o hldemux.o \
		bd_emu.o blockdecode.o blkidcache_mlvl.o partemu/partemu.o bd_flatflash.o hkpackets.o powerdown.o
TARGET=recv
CFLAGS=-ggdb -I ../common -I ../micro-ecc -I partemu -Og -DHOST_BUILD
LDFLAGS=-lmbedtls -lmbedcrypto

all: $(TARGET)

sha256.o: ../sha256/sha256.c ../sha256/sha256.h
	$(CC) $(CFLAGS) -c -o $@ $<

uECC.o: ../micro-ecc/uECC.c ../micro-ecc/uECC.h
	$(CC) $(CFLAGS) -c -o $@ $<

$(TARGET): $(OBJS)
	$(CC) -o $@ $^ $(LDFLAGS)

clean:
	rm -f $(OBJS) $(TARGET)
