# $NetBSD: Makefile,v 1.33 2017/09/18 09:53:04 maya Exp $

DISTNAME=	kwallet-${KF5VER}
PKGREVISION=	6
CATEGORIES=	security

HOMEPAGE=	https://community.kde.org/Frameworks
COMMENT=	Secure and unified container for user passwords
LICENSE=	gnu-lgpl-v2.1

.include "../../meta-pkgs/kf5/Makefile.common"

BUILD_DEPENDS+=	kdoctools>=${KF5VER}:../../devel/kdoctools

USE_TOOLS+=	msgmerge

.include "../../lang/python/tool.mk"
.include "../../devel/knotifications/buildlink3.mk"
.include "../../devel/kservice/buildlink3.mk"
.include "../../graphics/kiconthemes/buildlink3.mk"
.include "../../security/gpgmepp/buildlink3.mk"
.include "../../security/libgcrypt/buildlink3.mk"
.include "../../x11/qt5-qtbase/buildlink3.mk"
.include "../../mk/bsd.pkg.mk"
