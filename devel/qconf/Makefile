# $NetBSD: Makefile,v 1.36 2017/09/18 09:53:18 maya Exp $
#

DISTNAME=		qconf-2.0
PKGREVISION=		6
CATEGORIES=		devel
MASTER_SITES=		http://delta.affinix.com/download/
EXTRACT_SUFX=		.tar.bz2

MAINTAINER=		pkgsrc-users@NetBSD.org
HOMEPAGE=		http://delta.affinix.com/qconf/
COMMENT=		Configure script generator for qmake
LICENSE=		gnu-gpl-v2

USE_PKGLOCALEDIR=	yes
HAS_CONFIGURE=		yes
CONFIGURE_ARGS+=	--prefix=${PREFIX:Q}
USE_LANGUAGES=		c c++

DOCDIR=			${PREFIX}/share/doc/${PKGBASE}
EGDIR=			${PREFIX}/share/examples/${PKGBASE}
MAKE_ENV+=		INSTALL_ROOT=${DESTDIR:Q}

post-install:
	${INSTALL_DATA_DIR} ${DESTDIR}${DOCDIR}
	${INSTALL_DATA_DIR} ${DESTDIR}${EGDIR}
	${INSTALL_DATA} ${WRKSRC}/README.md ${DESTDIR}${DOCDIR}
	for fn in ${WRKSRC}/examples/*.qc; do			\
		${INSTALL_DATA} $${fn} ${DESTDIR}${EGDIR};	\
	done

.include "options.mk"

.include "../../mk/bsd.pkg.mk"
