################################################################################
#
#   Copyright (c) 2014 Minoca Corp. All Rights Reserved
#
#   Module Name:
#
#       Integrator/CP ACPI Tables
#
#   Abstract:
#
#       This module compiles the Integrator/CP ACPI tables.
#
#   Author:
#
#       Evan Green 7-Apr-2014
#
#   Environment:
#
#       Firmware
#
################################################################################

BINARY := acpi.ffs

BINARYTYPE = none

IASL = iasl

IASL_OPTIONS = -we

OBJS += dbg2.aml     \
        dsdt.aml     \
        facp.aml     \
        facs.aml     \
        incp.aml     \

include $(SRCROOT)/os/minoca.mk

$(BINARY): $(OBJS)
	@echo Generating - $@
	@cd $(OBJROOT)/$(THISDIR) && \
	 genffs -g 7E374E25-8E01-4FEE-87F2-390C23C606CD -r EFI_SECTION_RAW \
	 -t EFI_FV_FILETYPE_FREEFORM -o $@ $^

%.aml:%.asl
	@echo Compiling ASL - $<
	@$(IASL) $(IASL_OPTIONS) -p $(OBJROOT)/$(THISDIR)/$@ $< > $(OBJROOT)/$(THISDIR)/iaslout.txt

