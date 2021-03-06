# Created by: Olivier Cochard-Labbe <olivier@FreeBSD.org>
# $FreeBSD$

PORTNAME=	wbarconf
PORTVERSION=	0.7.2.2
PORTREVISION=	1
CATEGORIES=	x11
MASTER_SITES=	http://koti.kapsi.fi/ighea/wbarconf/

MAINTAINER=	olivier@FreeBSD.org
COMMENT=	Configuration GUI for wbar

BROKEN=		unfetchable
DEPRECATED=	Broken, uses EOLed python27
EXPIRATION_DATE=	2020-02-19

LICENSE=	GPLv3

RUN_DEPENDS=	wbar:x11/wbar

USE_GNOME=	pygobject pygtk2 gtk20
USES=		desktop-file-utils gettext gnome python:2.7 shebangfix
SHEBANG_FILES=	${WRKSRC}/wbarconf
python_OLD_CMD=	"/usr/bin/env python2"
NO_BUILD=	yes
WRKSRC=		${WRKDIR}/${PORTNAME}
PORTDOCS=	README COPYING
INSTALLS_ICONS=	yes

OPTIONS_DEFINE=	DOCS

do-install:
	${INSTALL_SCRIPT} ${WRKSRC}/${PORTNAME} ${STAGEDIR}${PREFIX}/bin
	${MKDIR} ${STAGEDIR}${DATADIR}
	${MKDIR} ${STAGEDIR}${DATADIR}/wbarbacks
	(cd ${WRKSRC}/wbarbacks/ && ${COPYTREE_SHARE} \* ${STAGEDIR}${DATADIR}/wbarbacks/)
	${INSTALL_DATA} ${WRKSRC}/messages.pot ${STAGEDIR}${DATADIR}
	${INSTALL_DATA} ${WRKSRC}/wbarconf.png ${STAGEDIR}${PREFIX}/share/pixmaps
	${INSTALL_DATA} ${WRKSRC}/wbarconf.desktop ${STAGEDIR}${PREFIX}/share/applications
	(cd ${WRKSRC}/locale/ && ${COPYTREE_SHARE} \* ${STAGEDIR}${PREFIX}/share/locale/)
	${MKDIR} ${STAGEDIR}${DOCSDIR}
	cd ${WRKSRC} && ${INSTALL_DATA} ${PORTDOCS} ${STAGEDIR}${DOCSDIR}

.include <bsd.port.mk>
