#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([flatpak-predefined-repos], [0.0.0], [BUG-REPORT-ADDRESS])

AM_INIT_AUTOMAKE([-Wno-portability subdir-objects foreign])

AC_ARG_WITH(repos,
  [AC_HELP_STRING([--with-repos], [repositories to make available])],
  [refkit_repos="${withval//,/ }"], [])

for r in ${refkit_repos}; do
    if test ! -e $srcdir/repos/$r.url; then
        AC_MSG_ERROR([missing URL file repos/$r.url for repository $r])
    fi
    if test ! -e $srcdir/repos/$r.key; then
        AC_MSG_ERROR([missing GPG key file repos/$r.key for repository $r])
    fi
    AC_MSG_NOTICE([including repository $r ($(cat $srcdir/repos/$r.url))...])
done

REFKIT_REPOS="$refkit_repos"
AC_SUBST([REFKIT_REPOS])

AC_OUTPUT(Makefile)

echo "Configuration:"

echo "* refkit repos: ${refkit_repos:-none}"
