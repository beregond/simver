Versioning
==========

Introduction
------------

Many projects have problem with version numbering scheme, what can be easily
seen in open source projects - each of them have a different one. One great
approach to make one consistent scheme is `SemVer <http://semver.org>`_.  What
you can see here is another approach, a bit different, but mostly inspired by
mentioned SemVer.

Definitions
-----------

The key words "must", "must not", "required", "shall", "shall not", "should",
"should not", "recommended", "may", and "optional" in this document are to be
interpreted as described in `RFC 2119 <http://tools.ietf.org/html/rfc2119>`_.

* **Chunks** - parts of version number (without suffix) separated by dot. In
  version 1.2.0.453-chuck-testa chuncks are 1, 2, 0 and 453.

* **Series** - releases corelated by first non-zero chunk in version number
  (releases with versions 0.1, 0.1.1, 1, 1.2, 1.3-dev are all released under
  series 1)

* **Unstable version** - release where version number points to revision, which
  work is found to be unstable, or its interfaces (like api) may change in the
  future. Unstable release is release that must not be used in production
  environment and its interfaces must not be base to build other components.

* **Stable version** - release where version number points to revision, which
  work is found to be stable (and preferably tested). If it is another stable
  version from given series it must keep backward compatibility with previous
  stable version(s) from given series.

* **Development version** - release where version number points to revision,
  which was developed after releasing first stable version, and has additional
  features or fixes, but is not yet fully tested, or is released for review. It
  must keep backward compatibility with series under which it was released, but
  may contain bugs or even not intended backward compatibility breaks.

Specification
-------------

* Every version number must take form of
  ``^(0.)?[1-9][0-9]*((.[0-9]*)*.[1-9][0-9]*)?(-[a-zA-Z][a-zA-Z-_0-9]*)?$``.
  (What gives you proper version numbers like 0.1, 2, 3, 3.1, 2.0.1-dev and wrong
  like 0.0.1, 2.0 or 2.0.0, 2.1-2 etc.)

* Every unstable version must have number that starts with ``0.X`` where ``X``
  is number of series, under which later stable versions will be released.

* Each chunk of version number must be consider as integer and must increase
  numerically (with exception for alphanumerical suffix, which, obviously, can't).
  For example: 1.9 -> 1.10 -> 1.11.

Examples
--------

This simple scheme may be at first difficult to understand, how to use it in
practice and solve many versioning problems, therefore please check examples
document to grasp more about it.
