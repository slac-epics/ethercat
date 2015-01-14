TOP=../..

include $(TOP)/configure/CONFIG

# build a program

SHARED_LIBRARIES=NO
STATIC_BUILD=YES

# work-around for ioc builder's benefit:
# the symbol below moved from $(TOP)/configure/RELEASE
VERSION=1-5-2dls5
#ETHERLAB=/afs/slac/g/lcls/package/linuxKernel_Modules/ethercat/$(VERSION)
#ETHERLAB_RT=/afs/slac/g/lcls/package/linuxKernel_Modules/ethercat/MAIN_TRUNK_linuxRT-x86
#ETHERLAB=/afs/slac/g/lcls/package/linuxKernel_Modules/ethercat/MAIN_TRUNK_linux-x86_64
ETHERLABPREFIX=$(ETHERLAB)/MAIN_TRUNK


#USR_INCLUDES_Linux += -I/afs/slac/g/lcls/package/linuxKernel_Modules/ethercat/MAIN_TRUNK_linux-x86_64/include
#USR_INCLUDES_Linux += -I/u/cd/mdewart/buildroot/output/staging/usr/include/libxml2
#USR_INCLUDES_Linux += -I/afs/slac/g/lcls/package/linuxKernel_Modules/ethercat/MAIN_TRUNK_linuxRT-x86/include 
#USR_INCLUDES_Linux += -I/u/cd/mdewart/buildroot/output/staging/usr/include


#USR_LDFLAGS_Linux += -L$(ETHERLAB)/lib/.libs -Wl,-rpath=$(ETHERLAB)/lib/.libs
#USR_LDFLAGS_Linux += -L$(ETHERLAB_RT)/lib/.libs -Wl,-rpath=$(ETHERLAB_RT)/lib/.libs
#USR_LDFLAGS += -L/usr/lib64
#USR_INCLUDES_Linux += -I/usr/include/libxml2
#USR_SYS_LIBS_Linux += xml2 ethercat
USR_SYS_LIBS_Linux += xml2 ethercat
#LIB_LIBS_Linux += $(ETHERLAB_RT)/lib/.libs/libethercat 
#LIB_LIBS_Linux += $(ETHERLAB)/lib/.libs/libethercat 
#LIB_LIBS_Linux += /usr/lib64 
xml2_DIR = $(LIBXML2_LIB)
ethercat_DIR = $(ETHERCAT_LIB)
USR_INCLUDES += $(ETHERCAT_INCLUDE)
USR_INCLUDES += $(LIBXML2_INCLUDE)
USR_LDFLAGS += $(ETHERCAT_LINK)
INC += classes.h parser.h classes.h unpack.h messages.h liberror.h
#INC += classes.h parser.h classes.h unpack.h messages.h

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
