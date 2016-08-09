# Only dexta and undexta, for use with bam2fasta.
THISDIR:=$(abspath $(dir $(realpath $(lastword ${MAKEFILE_LIST}))))
CFLAGS = -O3 -Wall -Wextra -Wno-unused-result -fno-strict-aliasing
LDLIBS+= -lm -lpthread
#LDFLAGS+= $(patsubst %,-L%,${LIBDIRS})
#ALL = dextract dexta undexta dexqv undexqv
ALL = dexta undexta
vpath %.c ${THISDIR}

#%: %.c

all: ${ALL}
dexta: dexta.o
undexta: undexta.o
${ALL}: DB.o QV.o

clean:
	rm -f ${ALL}
	rm -fr *.dSYM *.o

install:
	rsync -av ${ALL} ${PREFIX}/bin
symlink:
	ln -sf $(addprefix ${CURDIR}/,${ALL}) ${PREFIX}/bin

.PHONY: clean all
