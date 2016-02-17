TOP=../..

include $(TOP)/configure/CONFIG

USR_INCLUDES += $(LIBXML2_INCLUDE)
USR_INCLUDES += $(ETHERCAT_INCLUDE)

# ========================================================
# Let's Build the Library
# ========================================================
LIBRARY_IOC += ecAsyn 

# Sources to build ecAsyn
ecAsyn_SRCS += ecAsyn.cpp

xml2_DIR = $(LIBXML2_LIB)
ecAsyn_LIBS += xml2
ecAsyn_LIBS += asyn scannerlib rtutils
ecAsyn_LIBS += $(EPICS_BASE_IOC_LIBS)

INC += gadc.h

DBD += ecAsyn.dbd

# ========================================================
# Let's Build an IOC Application in here too
# ========================================================
PROD_LDFLAGS += $(LIBXML2_LINK)
PROD_SYS_LIBS += xml2

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
