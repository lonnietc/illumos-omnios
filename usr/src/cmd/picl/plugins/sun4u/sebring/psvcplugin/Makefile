#
# CDDL HEADER START
#
# The contents of this file are subject to the terms of the
# Common Development and Distribution License (the "License").
# You may not use this file except in compliance with the License.
#
# You can obtain a copy of the license at usr/src/OPENSOLARIS.LICENSE
# or http://www.opensolaris.org/os/licensing.
# See the License for the specific language governing permissions
# and limitations under the License.
#
# When distributing Covered Code, include this CDDL HEADER in each
# file and include the License file at usr/src/OPENSOLARIS.LICENSE.
# If applicable, add the following below this CDDL HEADER, with the
# fields enclosed by brackets "[]" replaced with your own identifying
# information: Portions Copyright [yyyy] [name of copyright owner]
#
# CDDL HEADER END
#
#
# Copyright 2009 Sun Microsystems, Inc.  All rights reserved.
# Use is subject to license terms.
#

include $(SRC)/Makefile.psm

# include library definitions
include $(SRC)/lib/Makefile.lib

ROOT_PLATFORM = $(USR_PLAT_DIR)/SUNW,Sun-Fire-V490
CHERRY_LINKTO_PLATFORM = SUNW,Sun-Fire-480R

include $(SRC)/cmd/picl/plugins/Makefile.com

ROOTLIBDIR =	$(ROOT_PLAT_PLUGINDIR)

.KEEP_STATE:

SUBDIRS=

all :=		TARGET= all
install :=	TARGET= install
clean :=	TARGET= clean
clobber :=	TARGET= clobber
lint :=		TARGET= lint
_msg :=		TARGET= _msg

all:

install: $(ROOTLIBDIR) all; $(MAKE) $(JAG_LINK)

_msg:	$(MSGDOMAIN)

$(MSGDOMAIN):
	$(INS.dir)

$(LIBLINKS):	FRC
	$(RM) $@; $(SYMLINK) $(DYNLIB) $@

# include library targets
include $(SRC)/lib/Makefile.targ
include $(SRC)/cmd/picl/plugins/Makefile.targ

$(SUBDIRS): FRC
	@cd $@; pwd; $(MAKE) $(TARGET)

FRC:

JAG_LINK=`cd $(ROOT_PLATFORM)/lib/picl/plugins/; \
echo $(ROOT_PLATFORM); \
rm -f libpsvcplugin_psr.so.1; \
rm -f libpsvcplugin_psr.so; \
ln -s ../../../../$(CHERRY_LINKTO_PLATFORM)/lib/picl/plugins/libpsvcplugin_psr.so.1 libpsvcplugin_psr.so.1; \
ln -s ../../../../$(CHERRY_LINKTO_PLATFORM)/lib/picl/plugins/libpsvcplugin_psr.so libpsvcplugin_psr.so;`
