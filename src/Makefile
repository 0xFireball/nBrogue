LIBTCOD_PATH=libtcod-1.5.1
LIBSDL_PATH=SDL-1.2.14

CC = gcc
CXX = g++

# Platform and binary
PLATFORM = LINUX

EXE = nBrogue
EXT = bin

ifeq ($(PLATFORM),WINDOWS)
  EXT = exe
endif

# Libraries
LIBS = -lSDL
ifeq ($(PLATFORM),WINDOWS)
  LIBS += -ltcod-mingw
endif
ifeq ($(PLATFORM),LINUX)
  LIBS += -ltcod
endif

CFLAGS=$(FLAGS) -I$(LIBTCOD_PATH)/include -I$(LIBSDL_PATH)/include -IBrogueCode -IPlatformCode -DBROGUE_TCOD -Wall -O2

OBJDIR=obj
SRCEXT := c
OBJEXT := o

SOURCES := $(shell find . -name \*.$(SRCEXT))
OBJECTS := $(addprefix $(OBJDIR)/, $(patsubst %.$(SRCEXT), %.$(OBJEXT), $(SOURCES)))

$(OBJDIR)/%.o: %.c
	$(info ($^))
	@mkdir -p $(dir $@)
	$(CC) $(CFLAGS) -c -o $@ $<

all: brogue

icon: $(NOOP)

brogue: $(OBJECTS) icon
	g++ -o $(EXE).$(EXT) ${OBJECTS} -L. -L$(LIBTCOD_PATH)/lib $(LIBS) -static-libgcc -static-libstdc++

clean:
	find . -name \*.o -type f -delete
	rm $(EXE).$(EXT)

.PHONY: clean
