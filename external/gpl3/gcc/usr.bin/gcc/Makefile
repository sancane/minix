#	$NetBSD: Makefile,v 1.2 2011/06/29 02:00:09 mrg Exp $

.include <bsd.own.mk>

PROG=           gcc
SRCS=		gccspec.c

CPPFLAGS+=	-I${BACKENDOBJ}

.if defined(__MINIX)
.if ${HAVE_LLVM:Uno} == "no"
SYMLINKS+=	gcc ${BINDIR}/cc
.endif # ${HAVE_LLVM:Uno} == "no"
.else
LINKS+=		${BINDIR}/gcc ${BINDIR}/cc 
.endif # defined(__MINIX)

MAN=		gcc.1
MLINKS=		gcc.1 cc.1 gcc.1 g++.1 gcc.1 c++.1

TEXINFO=	gcc.texi
INFOFLAGS=      -I${DIST}/gcc/doc -I${DIST}/gcc/doc/include

.include "../Makefile.frontend"

.PATH: ${DIST}/gcc ${DIST}/gcc/doc

.include <bsd.info.mk>

COPTS.builtins.c = -Wno-stack-protector

.if !defined(__MINIX)
LDADD+=		-lintl
DPADD+=		${LIBINTL}
.endif # !defined(__MINIX)

gcc.info: gcc-vers.texi
