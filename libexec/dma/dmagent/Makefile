.include <src.opts.mk>

LIBADD=	ssl crypto

PROG=	dma
SRCS=	aliases_parse.y \
	aliases_scan.l \
	base64.c \
	conf.c \
	crypto.c \
	dma.c \
	dns.c \
	local.c \
	mail.c \
	net.c \
	spool.c \
	util.c
MAN=	dma.8
MLINKS=	dma.8 dma.conf.5
CONFSMODE=	0640
CONFSGRP=	mail
CONFS=	auth.conf dma.conf
CONFSDIR=	${CONFDIR}/dma
CFLAGS+=	-DOPENSSL_API_COMPAT=0x10100000L
YFLAGS+=	-i
CLEANFILES=	aliases_parse.i
FILES=	mailer.conf
FILESDIR=	${SHAREDIR}/examples/dma

BINMODE=	2555

.include <bsd.compiler.mk>

.if ${COMPILER_TYPE} == gcc
WARNS?=	5
.endif

.include <bsd.prog.mk>
