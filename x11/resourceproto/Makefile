# $NetBSD: Makefile,v 1.5 2012/10/29 05:06:50 asau Exp $
#

DISTNAME=		resourceproto-1.2.0
CATEGORIES=		x11
MASTER_SITES=		${MASTER_SITE_XORG:=proto/}
EXTRACT_SUFX=		.tar.bz2

MAINTAINER=		joerg@NetBSD.org
HOMEPAGE=		http://xorg.freedesktop.org/
COMMENT=		Resource extension headers from X.org

CONFLICTS+=		resourceext-[0-9]*

GNU_CONFIGURE=		yes
PKGCONFIG_OVERRIDE+=	resourceproto.pc.in
USE_LANGUAGES=		c

.include "../../mk/bsd.pkg.mk"
