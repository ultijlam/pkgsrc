# $NetBSD: Makefile,v 1.9 2017/01/01 14:44:05 wiz Exp $

DISTNAME=	Mezzanine-1.2.4
PKGNAME=	${PYPKGPREFIX}-${DISTNAME:tl}
CATEGORIES=	www
MASTER_SITES=	${MASTER_SITE_PYPI:=M/Mezzanine/}

MAINTAINER=	ryoon@NetBSD.org
HOMEPAGE=	http://mezzanine.jupo.org/
COMMENT=	Open source content management platform on Django
LICENSE=	2-clause-bsd

DEPENDS+=	${PYPKGPREFIX}-flakes-[0-9]*:../../devel/py-flakes
DEPENDS+=	${PYPKGPREFIX}-postgresql-[0-9]*:../../databases/py-postgresql
DEPENDS+=	${PYPKGPREFIX}-pep8-[0-9]*:../../devel/py-pep8
DEPENDS+=	${PYPKGPREFIX}-imaging-[0-9]*:../../graphics/py-imaging
DEPENDS+=	${PYPKGPREFIX}-html5lib-[0-9]*:../../textproc/py-html5lib
DEPENDS+=	${PYPKGPREFIX}-pytz-[0-9]*:../../time/py-pytz
DEPENDS+=	${PYPKGPREFIX}-django-[0-9]*:../../www/py-django
DEPENDS+=	${PYPKGPREFIX}-django-appconf-[0-9]*:../../www/py-django-appconf
DEPENDS+=	${PYPKGPREFIX}-django-south-[0-9]*:../../www/py-django-south
DEPENDS+=	${PYPKGPREFIX}-bleach-[0-9]*:../../www/py-bleach
DEPENDS+=	${PYPKGPREFIX}-django-mezzanine-filebrowser-[0-9]*:../../www/py-django-mezzanine-filebrowser
DEPENDS+=	${PYPKGPREFIX}-django-mezzanine-grappelli-[0-9]*:../../www/py-django-mezzanine-grappelli

USE_PKGLOCALEDIR=	yes
USE_LANGUAGES=		# none

PYTHON_VERSIONS_INCOMPATIBLE=	34 35 36 # py-django-mezzanine-filebrowser, py-django-mezzanine-grappelli, py-imaging

MESSAGE_SUBST+=	PYTHONBIN=${PYTHONBIN}

.include "../../lang/python/application.mk"
.include "../../lang/python/distutils.mk"
.include "../../mk/bsd.pkg.mk"
