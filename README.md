UPDATEINFO.XML GENERATION
=========================

This utility eats a errata.latest.xml from the CEFS project and converts
it in to a useable updateinfo.xml that you can inject in to your CentOS
repositories. It is purpose built for a specific use case, but it can
be modified to suit your particular needs.


Usage
-----
You must set the configuration variables in the header of the script first.
Once you've done this, simply run:

```bash
generate_updateinfo.py /path/to/errata.latest.xml
```

It will write out a number of updateinfo.xml files in the 
BUILD_PREFIX/updateinfo-RELEASES/ directory.

You can now take the appropriate updateinfo.xml file and inject it in your
repository using the /usr/bin/modifyrepo command.

Example
-------
The following example illustrates how you would go about using this for a CentOS 6 repo.
The assumption is that you've set the BUILD_PREFIX=/security and that your CentOS-6-Updates
directory lives under /repositories/

```bash
wget -q -N -P/security http://cefs.steve-meier.de/errata.latest.xml

generate_updateinfo.py /security/errata.latest.xml

/usr/bin/modifyrepo /security/updateinfo-6/updateinfo.xml /repositories/CentOS-6-Updates/repodata
```

Authors
-------
Kristian Kostecky [http://vmfarms.com]


Copyright and license
---------------------

Copyright (C) 2013  Kristian K. [http://vmfarms.com] [kris@vmfarms.com]

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see [http://www.gnu.org/licenses/].
