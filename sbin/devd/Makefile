.include <src.opts.mk>

WARNS?= 6
PACKAGE=devd
CONFGROUPS=	CONFS DEVD
CONFS=	devd.conf
DEVD=	devmatch.conf
DEVDDIR=	/etc/devd
.if ${MK_ACPI} != "no"
DEVD+=	asus.conf
.endif

.if ${MK_AUTOFS} != "no"
CONFGROUPS+=		AUTOFS
AUTOFSDIR=		${DEVDDIR}
AUTOFS+=		autofs.conf
AUTOFSPACKAGE=		autofs
.endif

CONFGROUPS+=		DHCLIENT
DHCLIENTDIR=		${DEVDDIR}
DHCLIENT+=		dhclient.conf
DHCLIENTPACKAGE=	dhclient

CONFGROUPS+=		POWERPROFILE
POWERPROFILEDIR=	${DEVDDIR}
POWERPROFILE+=		power_profile.conf
POWERPROFILEPACKAGE=	acpi

CONFGROUPS+=		CONSOLE
CONSOLEDIR=		${DEVDDIR}
CONSOLE+=		moused.conf syscons.conf
CONSOLEPACKAGE=		console-tools

.if ${MK_BLUETOOTH} != "no"
CONFGROUPS+=		BLUETOOTH
BLUETOOTHDIR=		${DEVDDIR}
BLUETOOTH+=		bluetooth.conf
BLUETOOTHPACKAGE=	bluetooth
.endif

.if ${MK_HYPERV} != "no"
CONFGROUPS+=	HYPERV
HYPERVDIR=${DEVDDIR}
HYPERV+=	hyperv.conf
HYPERVPACKAGE=	hyperv-tools
.endif

CONFGROUPS+=		NVME
NVMEDIR=		${DEVDDIR}
NVME+=			nvmf.conf
NVMEPACKAGE=		nvme-tools

.if ${MK_USB} != "no"
DEVD+=	uath.conf ulpt.conf
.endif

.if ${MACHINE_ARCH} == "powerpc"
DEVD+=	apple.conf
.endif

.if ${MK_ZFS} != "no"
DEVD+=	zfs.conf
.endif

PROG_CXX=devd
SRCS=	devd.cc token.l parse.y y.tab.h
MAN=	devd.8 devd.conf.5

LIBADD=	util

YFLAGS+=-v
CFLAGS+=-I. -I${.CURDIR}
CFLAGS.clang += -Wno-missing-variable-declarations
CFLAGS.gcc = -Wno-redundant-decls
CXXFLAGS.gcc = -Wno-redundant-decls

CLEANFILES= y.output y.tab.i

HAS_TESTS=
SUBDIR.${MK_TESTS}+= tests

.include <bsd.prog.mk>
