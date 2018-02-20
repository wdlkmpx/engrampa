SUBDIRS = ui icons

desktopdir = $(datadir)/applications
desktop_DATA = engrampa.desktop

matchdir = $(datadir)/engrampa
match_DATA = packages.match

servicedir = $(datadir)/dbus-1/services
service_in_files = org.mate.Engrampa.service.in
service_DATA = $(service_in_files:.service.in=.service)
$(service_DATA): $(service_in_files) Makefile
	$(AM_V_GEN) $(SED) -e "s|\@libexecdir\@|$(libexecdir)|" $< > $@

appdatadir = $(datadir)/appdata
appdata_DATA = engrampa.appdata.xml

gsettingsschema_in_files = org.mate.engrampa.gschema.xml.in
gsettings_SCHEMAS = $(gsettingsschema_in_files:.xml.in=.xml)
.PRECIOUS: $(gsettings_SCHEMAS)

@GSETTINGS_RULES@

man_MANS = engrampa.1

EXTRA_DIST = \
       packages.match.in \
       packages.match \
       $(desktop_DATA) \
       $(gsettingsschema_in_files) \
       $(man_MANS) \
       $(service_in_files) \
       $(NULL)

DISTCLEANFILES = \
       $(service_DATA) \
       $(NULL)

CLEANFILES = \
       $(gsettings_SCHEMAS) \
       engrampa.appdata.xml \
       $(NULL)

dist-hook: 
	cd $(distdir); rm -f $(CLEANFILES)

-include $(top_srcdir)/git.mk
