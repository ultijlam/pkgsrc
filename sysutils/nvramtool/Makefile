# $NetBSD: Makefile,v 1.7 2017/09/03 08:53:15 wiz Exp $
#

DISTNAME=	nvramtool-4.0-9989-gf2dfef0-08bda29
PKGNAME=	nvramtool-0pre20150613
CATEGORIES=	sysutils
MASTER_SITES=	${MASTER_SITE_LOCAL:=nvramtool/}

MAINTAINER=	jakllsch@kollasch.net
HOMEPAGE=	https://www.coreboot.org/Nvramtool
COMMENT=	Coreboot CMOS NVRAM manipulation utility
LICENSE=	gnu-gpl-v2

USE_TOOLS+= gmake
USE_TOOLS+= date

USE_LANGUAGES+= c

.include "../../mk/bsd.prefs.mk"

ONLY_FOR_PLATFORM=	#Darwin-*-i386 Darwin*-x86_64 # would need DirectIO
ONLY_FOR_PLATFORM+=	FreeBSD-*-i386 FreeBSD-*-x86_64
ONLY_FOR_PLATFORM+=	Linux-*-i386 Linux-*-x86_64
ONLY_FOR_PLATFORM+=	NetBSD-*-i386 NetBSD-*-x86_64

WRKSRC=			${WRKDIR}/${DISTNAME}

BUILD_TARGET= nvramtool

INSTALLATION_DIRS=	sbin ${PKGMANDIR}/man8

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/nvramtool ${DESTDIR}${PREFIX}/sbin/nvramtool
	${INSTALL_MAN} ${WRKSRC}/cli/nvramtool.8 ${DESTDIR}${PREFIX}/${PKGMANDIR}/man8/nvramtool.8

.include "../../mk/bsd.pkg.mk"
