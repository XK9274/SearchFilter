.PHONY: build
.PHONY: clean

TARGET=kbinput
LIBTARGET=libkbinput.so

###########################################################

ifeq (,$(BUILD_DIR))
BUILD_DIR=.
endif

ifeq (,$(LIB_DIR))
LIB_DIR=.
endif

ifneq (,$(UNION_PLATFORM))
PLATFORM=$(UNION_PLATFORM)
endif

ifeq (,$(PLATFORM))
PLATFORM=linux
endif

###########################################################

CC = $(CROSS_COMPILE)g++
CFLAGS = -I../common -DVERSION=\"$(VERSION)\" -DPLATFORM_$(shell echo $(PLATFORM) | tr a-z A-Z) 
LIB_CFLAGS = $(CFLAGS) -fPIC
LDFLAGS = -s -lSDL -lSDL_image -lSDL_ttf -lrt
OPTM=-O3

build:
	$(CC) -o $(BUILD_DIR)/$(TARGET) main.cpp $(CFLAGS) $(LDFLAGS) $(OPTM) -ldl -rdynamic

lib:
	$(CC) -shared -o $(LIB_DIR)/$(LIBTARGET) main.cpp $(LIB_CFLAGS) $(LDFLAGS) $(OPTM)

clean:
	rm -f $(BUILD_DIR)/$(TARGET) $(LIB_DIR)/$(LIBTARGET)
