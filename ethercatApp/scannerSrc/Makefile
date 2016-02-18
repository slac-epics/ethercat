TOP=../..

include $(TOP)/configure/CONFIG

# build a program

# work-around for ioc builder's benefit:
# the symbol below moved from $(TOP)/configure/RELEASE
VERSION=1-5-2dls5
ETHERLABPREFIX=$(ETHERLAB)/MAIN_TRUNK


z_DIR = $(ZLIB_LIB)
lzma_DIR = $(XZ_LIB)
xml2_DIR = $(LIBXML2_LIB)
ethercat_DIR=$(ETHERCAT_LIB)

USR_LIBS_Linux += xml2 z lzma
USR_LIBS_Linux += ethercat

USR_INCLUDES += $(ETHERCAT_INCLUDE)

USR_INCLUDES += $(ZLIB_INCLUDE)
USR_INCLUDES += $(XZ_INCLUDE)
USR_INCLUDES += $(LIBXML2_INCLUDE)


INC += classes.h parser.h classes.h unpack.h messages.h liberror.h

LIBRARY += scannerlib
scannerlib_SRCS += parser.c classes.c unpack.c

PROD += scanner
# need private header file to disable errors being sent to stderr
#scanner_INCLUDES += -I$(ETHERLAB)/src/ethercat-$(subst -,.,$(VERSION))/lib
scanner_INCLUDES_Linux += -I$(ETHERLAB_RT)/lib
scanner_INCLUDES_Linux += -I$(ETHERLAB)/lib
scanner_SRCS += scanner.c simulation.c
scanner_LIBS += rtutils scannerlib Com

PROD += serialtool
# need private header files for the serial number write IOCTL
#serialtool_INCLUDES += -I$(ETHERLAB)/src/ethercat-$(subst -,.,$(VERSION))/master
serialtool_INCLUDES_Linux += -I$(ETHERLAB_RT)/master
serialtool_INCLUDES_Linux += -I$(ETHERLAB)/master
serialtool_SRCS += serialtool.c

PROD += slaveinfo

slaveinfo_SRCS += slaveinfo.c

include $(TOP)/configure/RULES
