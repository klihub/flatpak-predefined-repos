REPODIR  = ${top_srcdir}/repos
REPOS    = @REFKIT_REPOS@
keydir   = ${sysconfdir}/flatpak-session
key_DATA = $(foreach r,$(REPOS),${REPODIR}/$(r).url ${REPODIR}/$(r).key)

all:

install-data-hook:
	if [ -n "$(REPOS)" ]; then \
	    chmod og-w $(DESTDIR)${keydir}/*; \
	else \
	    mkdir -p $(DESTDIR)${keydir} ; \
	    touch $(DESTDIR)${keydir}/__no_predefined_repos__ ; \
	fi
