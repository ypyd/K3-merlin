include ../common.mak

all:

install:
	install -d $(INSTALLDIR)/sbin
	install -d $(INSTALLDIR)/usr/sbin
	install -d $(INSTALLDIR)/lib

ifeq ($(TCONFIG_USB),y)
# Optware perl symlink
	install -d $(INSTALLDIR)/usr/bin
	ln -sf /opt/bin/perl $(INSTALLDIR)/usr/bin/perl
endif

# add ddns
	install -d $(INSTALLDIR)/usr/bin
	install -m 0755 ddns.sh $(INSTALLDIR)/usr/bin

# cron helper
	install -m 0700 cru $(INSTALLDIR)/usr/sbin

# playing with ipkg / from OpenWrt svn
#!!TB	install -m 0700 ipkg $(INSTALLDIR)/usr/sbin

# system info
	install -m 0700 sysinfo $(INSTALLDIR)/usr/sbin

# keep winscp happy
#	install -m 0700 groups $(INSTALLDIR)/usr/bin

# chpasswd script
	install -m 0700 chpasswd.sh $(INSTALLDIR)/usr/sbin

# Easy-rsa scripts (for OpenVPN)

ifeq ($(RTCONFIG_OPENVPN),y)
	install -m 0700 setuprsa.sh $(INSTALLDIR)/usr/sbin
	install -m 0700 -D updown.sh $(INSTALLDIR)/usr/sbin
	install -m 0700 -D vpnrouting.sh $(INSTALLDIR)/usr/sbin
endif

# K3screenctrl setup script
	ln -sf /tmp/k3screenctrl $(INSTALLDIR)/lib/k3screenctrl

# K3 nvram & wl setup script
	install -m 0700 k3nv.sh $(INSTALLDIR)/usr/sbin
	install -m 0700 k3wl $(INSTALLDIR)/usr/sbin

# Entware setup script
	install -m 0700 entware_install.sh $(INSTALLDIR)/usr/sbin
	install -m 0700 entware-setup.sh $(INSTALLDIR)/usr/sbin

# Postconf helper script
	#install -m 0755 helper.sh $(INSTALLDIR)/usr/sbin

ifeq ($(RTN14U)$(RTAC52U)$(RTAC51U)$(RTN11P)$(RTN300)$(RTN54U)$(RTAC1200HP)$(RTN56UB1)$(RTN56UB2)$(RTAC54U),y)
# for read/write Ralink PHY registers
        install -D mii_mgr $(INSTALLDIR)/bin/mii_mgr
endif

# Adaptive QoS tc patch
ifeq ($(RTCONFIG_BCMARM),y)
	install -m 0700 -D faketc $(INSTALLDIR)/usr/sbin
endif

clean:
