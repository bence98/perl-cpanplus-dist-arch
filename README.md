-*- org -*-
:   ____ ____   _    _   _          ____  _     _          _             _     
:  / ___|  _ \ / \  | \ | |  _  _ _|  _ \(_)___| |_ _ _   / \   _ __ ___| |__  
: | |   | |_) / _ \ |  \| |_| |(_|_) | | | / __| __(_|_) / _ \ | '__/ __| '_ \ 
: | |___|  __/ ___ \| |\  |_   _| _| |_| | \__ \ |_ _ _ / ___ \| | | (__| | | |
:  \____|_| /_/   \_\_| \_| |_|(_|_)____/|_|___/\__(_|_)_/   \_\_|  \___|_| |_|
: 

[![CPANPLUS::Dist::Arch](https://github.com/jnbek/perl-cpanplus-dist-arch/actions/workflows/ci.yml/badge.svg)](https://github.com/jnbek/perl-cpanplus-dist-arch/actions/workflows/ci.yml)


CPANPLUS::Dist::Arch - CPANPLUS backend for building Archlinux pacman packages

* Background

CPAN is the name for both the repository of Perl modules mirrored
around the world and the program that automatically installs modules
from that international module list. CPANPLUS is the next evolution
of the venerable CPAN shell.

ArchLinux is a Linux distribution known for its minimalism. The most
distinguishing feature of ArchLinux is its use of the "pacman" package
managing program. Packages for pacman are created with the "makepkg"
script which is included with "pacman".

CPANPLUS::Dist::Arch is a plugin whose goal is to bridge the gap
between the CPAN and ArchLinux. CPANPLUS is already a great tool for
downloading modules, resolving dependencies, and installing modules.
This module acts as a plugin, installing itself into the CPANPLUS
internals and managing the module building and installation process.

Instead of CPANPLUS's usual behavior, Perl modules are instead built as
ArchLinux packages by using "makepkg". Instead of the straight-forward
installation of modules by copying files into system-wide locations,
these built packages are installed using "pacman". This offers the
advantage of better dependency tracking and uninstallation.

* Install

To install this module manually follow these steps. If you have
already downloaded and extracted the distribution tarball
(CPANPLUS-Dist-Arch-<version>.tar.gz) in order to read this README
file, skip to step 4.

1) Download the distribution tarball from CPAN.
2) Extract the tarball.
3) *cd* into the extracted directory (CPANPLUS-Dist-Arch-<version>)
4) Run *perl Build.PL* to create the *Build* file.
5) Run *./Build* to build the module using the *Build* file.
6) (Optional) Run *./Build test* to run automated self-tests.
7) Run *./Build install* to install the perl module into a system directory.

#+BEGIN_EXAMPLE

curl -O http://.../CPANPLUS-Dist-Arch-X.XX.tar.gz
tar xf CPANPLUS-Dist-Arch-X.XX.tar.gz
cd CPANPLUS-Dist-Arch-X.XX
perl Build.PL
./Build
./Build test
sudo ./Build install

#+END_EXAMPLE

Or better yet, use a CPAN shell to do it for you! CPANminus is
available on CPAN under the name "App-cpanminus".

* Setup CPANPLUS

The steps above install this module into your system where it is
available for use by perl. You will also need to activate
CPANPLUS::Dist::Arch as a plugin to the CPANPLUS shell.

I have included a program called 'setupdistarch' that makes this
easier. Run the program and answer yes in order to enable
automatic packaging of installed CPANPLUS modules.

#+BEGIN_EXAMPLE

$ setupdistarch
Are you sure you want to auto-package CPAN installs? [Yn] y
CPANPLUS will now auto-package modules.

#+END_EXAMPLE

See the 'setupdistarch' manpage for more information.

* Requirements

A number of modules are required to run CPANPLUS::Dist::Arch. These
are all included with recent versions of perl so you should not need
to install anything before you can use it.

** Core Modules

   - CPANPLUS
   - Digest::MD5
   - Pod::Select
   - List::Util
   - File::Path
   - File::Copy
   - File::stat
   - DynaLoader
   - IPC::Cmd
   - version
   - English
   - Carp
   - Cwd

** Optional Template Modules

C::D::A uses templates for creating PKGBUILD files. It is possible to
override the template that is used in order to customize PKGBUILDs
completely to your liking. If you do this you might want to use a
template module instead of C::D::A's crude internal template
engine. Template modules are searched for in this order:

|----------+-------------------+-------------------|
| Priority | Module            | CPAN Distribution |
|----------+-------------------+-------------------|
|        1 | Template::Toolkit | Template          |
|        2 | Template::Alloy   | Template-Alloy    |
|        3 | Template::tiny    | Template-Tiny     |
|----------+-------------------+-------------------|

* See Also

** CPANPLUS::Dist::Arch manpage

Run 'man CPANPLUS::Dist::Arch' after installing to view the manpage.

** Arch Package in [community] : perl-cpanplus-dist-arch

https://www.archlinux.org/packages/community/any/perl-cpanplus-dist-arch/

** Git Repository

http://github.com/jnbek/perl-cpanplus-dist-arch

** Archlinux Perl Package Guidelines

http://wiki.archlinux.org/index.php/Perl_Package_Guidelines

** pacman

http://wiki.archlinux.org/index.php/Pacman

** makepkg

http://wiki.archlinux.org/index.php/Makepkg

** CPANPLUS

http://search.cpan.org/dist/CPANPLUS/

* Author

Created by: Justin Davis <juster at cpan dot org>

Serendipitously maintained by: John D Jones III <jnbek at cpan dot org>

* Support

Send me an e-mail if you have any questions or need help. If you
run into any bugs please e-mail any information about them.

* License and Copyright

Copyright 2013 Justin Davis.

Copyright 2015 John D Jones III

This program is free software; you can redistribute it and/or modify it
under the terms of either: the GNU General Public License as published
by the Free Software Foundation; or the Artistic License.

See http://dev.perl.org/licenses/ for more information.
