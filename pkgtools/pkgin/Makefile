# $NetBSD: Makefile,v 1.72 2017/09/18 09:53:33 maya Exp $

DISTNAME=		pkgin-0.9.4
GITHUB_TAG=		v${PKGVERSION_NOREV}
PKGREVISION=		7
CATEGORIES=		pkgtools
MASTER_SITES=		${MASTER_SITE_GITHUB:=NetBSDfr/}

MAINTAINER=		imil@NetBSD.org
HOMEPAGE=		http://pkgin.net/
COMMENT=		Apt / yum like tool for managing pkgsrc binary packages
LICENSE=		modified-bsd

EGDIR=			${PREFIX}/share/examples/${PKGBASE}
CONF_FILES=		${EGDIR}/repositories.conf.example		\
			${PKG_SYSCONFDIR}/${PKGBASE}/repositories.conf

OWN_DIRS+=		${PKG_SYSCONFDIR}/${PKGBASE}
INSTALLATION_DIRS+=	bin ${PKGMANDIR}/cat1 ${PKGMANDIR}/man1 ${EGDIR}

BUILD_DEFS+=		PKGIN_REPOSITORY_URL
BUILD_DEFS+=		VARBASE

OWN_DIRS+=		${VARBASE}/db/pkgin

SUBST_CLASSES+=		path
SUBST_STAGE.path=	pre-configure
SUBST_MESSAGE.path=	Adjusting path.
SUBST_FILES.path=	Makefile.in actions.c pkgin.1
SUBST_SED.path=		-e "s|/usr/pkg/etc|${PKG_SYSCONFDIR}|g"
SUBST_SED.path+=	-e "s|/usr/sbin|${PKG_TOOLS_BIN}|g"
SUBST_SED.path+=	-e "s|/var|${VARBASE}|g"
SUBST_SED.path+=	-e "s|/usr/pkg|${PREFIX}|g"
SUBST_SED.path+=	-e "s|!=.*uname -p|=	${MACHINE_ARCH}|g"

GNU_CONFIGURE=		yes
USE_FEATURES=		nbcompat
USE_TOOLS+=		nroff

.include "../../mk/bsd.prefs.mk"

SUBST_CLASSES.NetBSD+=	osrel
SUBST_STAGE.osrel=	pre-configure
SUBST_MESSAGE.osrel=	Adjusting repository OS release
SUBST_FILES.osrel=	REPOSITORIES
SUBST_SED.osrel=	-e "s|@OSREL@|${OS_VERSION:C/_.*//}|"

CFLAGS.SunOS+=		-D_FILE_OFFSET_BITS=64

MAKE_ENV+=		MACHINE_ARCH=${MACHINE_ARCH}

DEPENDS+=		pkg_install>=20130901:../../pkgtools/pkg_install

# those have official repositories
.if !empty(PKGIN_REPOSITORY_URL)
pre-install:
	${ECHO} ${PKGIN_REPOSITORY_URL} >> ${WRKSRC}/repositories.conf
.elif ${OPSYS} == "NetBSD" || ${OPSYS} == "DragonFly" || ${OPSYS} == "Minix"
pre-install:
	${GREP} -i ${OPSYS} ${WRKSRC}/REPOSITORIES >> 			\
		${WRKSRC}/repositories.conf
.endif

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/pkgin ${DESTDIR}${PREFIX}/bin
	${INSTALL_MAN} ${WRKSRC}/pkgin.1				\
		${DESTDIR}${PREFIX}/${PKGMANDIR}/man1
.if !empty(MANINSTALL:Mcatinstall)
.  if defined(CATMAN_SECTION_SUFFIX) && !empty(CATMAN_SECTION_SUFFIX:M[Yy][Ee][Ss])
	${INSTALL_MAN} ${WRKSRC}/pkgin.cat1				\
		${DESTDIR}${PREFIX}/${PKGMANDIR}/cat1/pkgin.1
.  else
	${INSTALL_MAN} ${WRKSRC}/pkgin.cat1				\
		${DESTDIR}${PREFIX}/${PKGMANDIR}/cat1/pkgin.0
.  endif
.endif
	${INSTALL_DATA} ${WRKSRC}/repositories.conf			\
		${DESTDIR}${EGDIR}/repositories.conf.example
	${INSTALL_DATA} ${WRKSRC}/preferred.conf			\
		${DESTDIR}${EGDIR}/preferred.conf.example

# libfetch has no builtin.mk and is included in NetBSD>=5
.if ${OPSYS} != "NetBSD" || \
	(${OPSYS} == "NetBSD" && !empty(OS_VERSION:M[0-4].*))
.	include "../../net/libfetch/buildlink3.mk"
.endif

.include "../../archivers/libarchive/buildlink3.mk"
.include "../../databases/sqlite3/buildlink3.mk"
.include "../../net/libfetch/buildlink3.mk"
.include "../../security/openssl/buildlink3.mk"
.include "../../mk/bsd.pkg.mk"
