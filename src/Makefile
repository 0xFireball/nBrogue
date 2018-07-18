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

CFLAGS=$(FLAGS) -I$(LIBTCOD_PATH)/include -I$(LIBSDL_PATH)/include -IBrogueCode -IPlatformCode -DBROGUE_TCOD -Wall

%.o : %.c
	$(CC) $(CFLAGS) -O2 -s -o $@ -c $<

OBJS=BrogueCode/Architect.o \
	BrogueCode/Combat.o \
	BrogueCode/Dijkstra.o \
	BrogueCode/Globals.o \
	BrogueCode/IO.o \
	BrogueCode/Buttons.o \
	BrogueCode/MainMenu.o \
	BrogueCode/Grid.o \
	BrogueCode/Time.o \
	BrogueCode/Items.o \
	BrogueCode/Light.o \
	BrogueCode/Monsters.o \
	BrogueCode/Movement.o \
	BrogueCode/RogueMain.o \
	BrogueCode/Random.o \
	BrogueCode/Recordings.o \
	PlatformCode/main.o \
	PlatformCode/platformdependent.o \
	PlatformCode/tcod-platform.o 

all: brogue

icon: $(NOOP)

brogue: ${OBJS} icon
	g++ -o $(EXE).$(EXT) ${OBJS} -L.  -L$(LIBTCOD_PATH)/lib $(LIBS) -static-libgcc -static-libstdc++

clean:
	find . -name \*.o -type f -delete
	rm $(EXE).$(EXT)

.PHONY: clean
