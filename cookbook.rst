Examples
========

Examples below are just suggestions, on how can you organize your workflow.
Remember that you can always adapt this scheme and examples to fit best to your
current needs.

Basic case
----------

First usable version should be ``0.1``, and later releases (not yes stable)
like ``0.1.1``, ``0.1.2`` and so on (or if there is a need ``0.1.1.3`` etc.).
When there is a moment, that you want to release alpha, beta and rc candidate,
just don't add any unnecessary suffixes like 'alpha' or 'beta', just release
next versions like ``0.1.5``, or ``0.1.5.1`` if these are next rc releases (for
knowing why there are no suffixes like 'alpha', 'beta' and so on see 'Automated
updates' example).

When you have release candidate, that is accepted, with, for example version
number like ``0.1.5.3`` just release version ``1`` which points to the same
revision.

After that, anytime you release new version you need just add ``1`` to second
chunk, so you can release versions ``1.1``, ``1.2``, ``1.3`` and so on. For
smaller fixes you can increment third chunk (SemVer strategy on major, minor
and patch would fit here very good).

Assume that current version is ``1``. Time comes when you need to release
version to public, but it's development version and you don't want anybody to
assume that this is version they should have have. In that situation it's good
to use suffixes, and since next milestone is ``1.1`` you can release your
version as ``1.0.1-dev``. Note that suffix ``-dev`` is just convention, you can
name it whatever you want, or have multiple development branches for different
features you want to release to get review or feedback on them before you merge
them into stable branch. If you want to release another version on that branch,
for example after fixing some bug, you can release ``1.0.2-dev`` or
``1.0.1.1-dev`` - in fact it is just your decision what fits better for you.
After you are done and new features are to be merged into stable branch, just
do it and release version ``1.1``. Remember that you can of course merge it
later, into release like ``1.4`` or further.

What is very important, first release that breaks backward compatibility must
be released under different series. If it is unstable release (since you want
to have some time for development) it should have number ``0.2``. Now you and
every user know it is unstable release for next series and that he shouldn't
use it yet. From here on, the rest of the process is the same: release first
stable version from series ``2``, releasing dev versions like
``2.0.3-something``, releasing next stable versions and at last releasing first
version under next series.

Automated updates
-----------------

With this scheme it is easy to make automated updates of your server. Of course
you won't find here implementation in any language or for certain package
manager, just a general idea.  Since version number, besides branch suffix,
consist only of integers and dots, all you need is to set up updater, that will
install/fetch new version from given branch every time version with higher precedence occur.

It comes handy when you have few development servers, which allows you to test
some features each from different branch. These servers can be even dedicated
to single developers. Each time developer releases version, which he find
is good enough, he releases some version in given series and branch. Server
dedicated to that certain series and branch now knows that new version was
released and can determine by version number if its newer release. If so, it
just updates it.

For example we could have server that install new package every time its version
number is from series ``1`` and from branch ``dev-steve`` (so matching version
number would be ``1.3.0.3-dev-steve``).

You can also have script for only stable releases (only for versions ``X.*``),
or only for unstable (``0.X.*``), but then you must remember that from releases
from series ``X`` takes both forms.
