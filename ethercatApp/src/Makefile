TOP=../..

include $(TOP)/configure/CONFIG

# ========================================================
# Let's Build the Library
# ========================================================
LIBRARY_IOC += ecAsyn 

# Sources to build ecAsyn
ecAsyn_SRCS += ecAsyn.cpp gadc.cpp

xml2_DIR = $(LIBXML2_LIB)
ecAsyn_LIBS += xml2
ecAsyn_LIBS += asyn scannerlib rtutils

INC += gadc.h

DBD += ecAsyn.dbd

# ========================================================
# Let's Build an IOC Application in here too
# ========================================================
PROD_IOC += ethercat
ethercat_DBD += base.dbd ecAsyn.dbd
ethercat_SRCS += ethercat_registerRecordDeviceDriver.cpp
USR_INCLUDES += $(LIBXML2_INCLUDE)
USR_INCLUDES += $(ETHERCAT_INCLUDE)
ecAsyn_INCLUDES += -I../../include

# These two lines are needed for non-vxWorks builds, such as Linux
ethercat_SRCS_DEFAULT += ethercatMain.cpp
ethercat_SRCS_vxWorks += -nil-

# ===================================
# Need to link libraries
# ===================================
ethercat_LIBS += ecAsyn asyn
ethercat_LIBS += $(EPICS_BASE_IOC_LIBS)

include $(TOP)/configure/RULES
