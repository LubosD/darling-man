#
# Generated automatically from Makefile.in by the
# configure script.
#

all:	../src/makemsg gencat
	@for i in mess.??; do ../src/makemsg -c $$i $$i.catin; \
	cat $$i.codeset $$i.catin > $$i.catin2; \
	echo "==== Making $$i.cat ====" ;\
	LC_ALL=en_US.UTF-8 ./gencat $$i.cat $$i.catin2; done; \
	rm -f core *.catin *.catin2

install:
	sh ./inst.sh "en" "$(DESTDIR)"

clean:
	rm -f gencat gencat.out core *~ *.cat *.catin *.catin2

spotless:
	rm -f Makefile

# Various versions of libc use different format message catalog files
# So we have to use the installed /usr/bin/gencat if possible.
# On the other hand, /usr/bin/gencat doesnt work in glibc 2.0.7
# The source in ../gencat is OK for libc4 and libc5, not for glibc.
gencat:
	if [ -f /usr/bin/gencat ]; then \
		if gencat gencat.out gencat.in 2>/dev/null; then \
			ln -s /usr/bin/gencat gencat; \
		else \
			cp gencat207fix.sh gencat; \
		fi \
	else \
		ln -s ../gencat/gencat gencat; \
		cd ../gencat; \
		make; \
	fi

