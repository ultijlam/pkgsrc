# $NetBSD: Makefile,v 1.30 2017/09/26 14:23:16 wiz Exp $

DISTNAME=	Devel-Cover-1.27
PKGNAME=	p5-${DISTNAME}
CATEGORIES=	devel perl5
MASTER_SITES=	${MASTER_SITE_PERL_CPAN:=Devel/}

MAINTAINER=	pkgsrc-users@NetBSD.org
HOMEPAGE=	http://search.cpan.org/dist/Devel-Cover/
COMMENT=	Perl 5 module providing code coverage metrics
LICENSE=	${PERL5_LICENSE}

DEPENDS+=	p5-PPI-HTML>=1.07:../../textproc/p5-PPI-HTML
DEPENDS+=	p5-Perl-Tidy>=20060719:../../devel/p5-Perl-Tidy
DEPENDS+=	p5-Pod-Coverage>=0.06:../../textproc/p5-Pod-Coverage
DEPENDS+=	p5-Template-Toolkit>=2.0:../../www/p5-Template-Toolkit
BUILD_DEPENDS+=	p5-Test-Differences-[0-9]*:../../devel/p5-Test-Differences

USE_LANGUAGES=		c
PERL5_PACKLIST=		auto/Devel/Cover/.packlist

.include "../../lang/perl5/module.mk"
.include "../../mk/bsd.pkg.mk"
