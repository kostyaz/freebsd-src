PROG=	mfiutil
LINKS=	${BINDIR}/mfiutil ${BINDIR}/mrsasutil

SRCS=	mfiutil.c mfi_bbu.c mfi_cmd.c mfi_config.c mfi_drive.c mfi_evt.c \
	mfi_flash.c mfi_patrol.c mfi_show.c mfi_volume.c mfi_foreign.c \
	mfi_properties.c
MAN=	mfiutil.8
MLINKS=	mfiutil.8 mrsasutil.8

CFLAGS.gcc+= -fno-builtin-strftime

LIBADD=	sbuf util

# Here be dragons
.ifdef DEBUG
CFLAGS+= -DDEBUG
.endif

.include <bsd.prog.mk>
