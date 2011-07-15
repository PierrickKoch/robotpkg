# robotpkg Makefile for:	lang/python3
# Created:			Séverin Lemaignan on Mon, 7 Dec 2009
#

PKGVERSION=	3.1.2
PKGREVISION=	1
DISTNAME=	Python-${PKGVERSION_NOREV}
PKGNAME=	python31-${PKGVERSION}
MASTER_SITES=	http://www.python.org/ftp/python/${PKGVERSION}/
EXTRACT_SUFX=   .tgz

MAINTAINER=	openrobots@laas.fr
CATEGORIES=	lang
HOMEPAGE=	http://www.python.org/
COMMENT=	Interpreted, interactive, object-oriented programming language
LICENSE=	psfl-v2

CONFLICTS+=	python3-[0-9]*
USE_LANGUAGES=	c c++

GNU_CONFIGURE=	yes
CONFIGURE_ARGS+=--with-threads
CONFIGURE_ARGS+=--enable-shared
CONFIGURE_ARGS+=--with-system-ffi
RPATH_DIRS=	lib

# Install only suffixed binaries and files
INSTALL_TARGET=	altinstall

SUBST_CLASSES+=		interp
SUBST_STAGE.interp=	post-extract
SUBST_MESSAGE.interp=	Replacing python interpreter path in scripts
SUBST_FILES.interp=	Lib/cgi.py	# explicitly demanded to be patched
SUBST_FILES.interp+=	Lib/test/test_bz2.py
SUBST_FILES.interp+=	Lib/test/test_largefile.py Lib/test/test_optparse.py
SUBST_SED.interp=	'1s|.*python[^ \t]*|\\\#!${PREFIX}/bin/python3.1|'

include ../../mk/sysdep/gdbm.mk
include ../../mk/sysdep/openssl.mk
include ../../mk/robotpkg.mk