TOP=../..

include $(TOP)/configure/CONFIG

USR_INCLUDES += $(LIBXML2_INCLUDE)
USR_INCLUDES += $(ETHERCAT_INCLUDE)

# ========================================================
# Let's Build the Library
# ========================================================
LIBRARY_IOC += ecAsyn 

# Sources to build ecAsyn
ecAsyn_SRCS += ecAsyn.cpp gadc.cpp

z_DIR = $(ZLIB_LIB)
lzma_DIR = $(XZ_LIB)
xml2_DIR = $(LIBXML2_LIB)

USR_LIBS_Linux += xml2 z lzma

USR_INCLUDES += $(ZLIB_INCLUDE)
USR_INCLUDES += $(XZ_INCLUDE)
USR_INCLUDES += $(LIBXML2_INCLUDE)

ecAsyn_LIBS += asyn scannerlib rtutils
ecAsyn_LIBS += $(EPICS_BASE_IOC_LIBS)

INC += gadc.h

DBD += ecAsyn.dbd

# ========================================================
# Let's Build an IOC Application in here too
# ========================================================

PROD_IOC += ethercatIOC

ethercatIOC_DBD += base.dbd ecAsyn.dbd

# Registration, IOC Shell and MAIN
ethercatIOC_SRCS_DEFAULT += ethercatIOC_registerRecordDeviceDriver.cpp ethercatIOCMain.cpp

# Generic ADC driver;  TDI-CTRL-REQ-015
ethercatIOC_SRCS += gadc.cpp

# ===================================
# Need to link libraries
# ===================================
ethercatIOC_LIBS += ecAsyn asyn 
ethercatIOC_LIBS += scannerlib rtutils
ethercatIOC_LIBS += $(EPICS_BASE_IOC_LIBS)

include $(TOP)/configure/RULES
