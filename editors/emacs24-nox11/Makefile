# $NetBSD: Makefile,v 1.11 2017/07/23 18:47:09 dholland Exp $

PKGNAME=	${DISTNAME:S/emacs/emacs24/:S/-/-nox11-/}
PKGREVISION=	2

CONFLICTS+=	emacs24-[0-9]*

FILESDIR=	${.CURDIR}/../../editors/emacs24/files
PATCHDIR=	${.CURDIR}/../../editors/emacs24/patches
PKGDIR=		${.CURDIR}/../../editors/emacs24

.include "../../editors/emacs24/Makefile.common"

CONFIGURE_ARGS+=	--without-dbus --without-m17n-flt --without-otf
CONFIGURE_ARGS+=	--without-rsvg --without-x --without-xft
CONFIGURE_ARGS+=	--without-gif --without-jpeg --without-png
CONFIGURE_ARGS+=	--without-tiff --without-xpm

.include "../../mk/bsd.pkg.mk"
