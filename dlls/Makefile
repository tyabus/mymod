#
# Half-Life Standard SDK 2.3 mp_i386.so Makefile for i386 Linux
#
# October 2002 by Leon Hartwig (hartwig@valvesoftware.com)
#

#make sure this is the correct compiler for your system
CXX?=g++
CC?=gcc

ARCH = $(shell uname -m)

DLLNAME = mp.so

# check for i386
ifeq ($(ARCH), i386)
        CFLAGS = -march=i686
endif

# check for x86_64
ifeq ($(ARCH), x86_64)
        LDFLAGS = -m32
        CFLAGS = -march=i686 -m32
endif

DLL_SRCDIR=.
ENGINE_SRCDIR=../engine
COMMON_SRCDIR=../common
PM_SHARED_SRCDIR=../pm_shared
GAME_SHARED_SRCDIR=../game_shared

DLL_OBJDIR=$(DLL_SRCDIR)/obj
PM_SHARED_OBJDIR=$(PM_SHARED_SRCDIR)/obj
GAME_SHARED_OBJDIR=$(GAME_SHARED_SRCDIR)/obj

BASE_CFLAGS=	-Dstricmp=strcasecmp -D_strnicmp=strncasecmp -Dstrnicmp=strncasecmp -fPIC \
		-DCLIENT_WEAPONS -Wno-invalid-offsetof -fpermissive

# optimization stuff
CFLAGS+=$(BASE_CFLAGS) -w -O2 -funsafe-loop-optimizations -funsafe-math-optimizations -s

INCLUDEDIRS=-I. -I$(ENGINE_SRCDIR) -I$(COMMON_SRCDIR) -I$(PM_SHARED_SRCDIR) -I$(GAME_SHARED_SRCDIR)

LDFLAGS+=-Wl,--no-undefined -shared -lm

DO_CXX=$(CXX) $(CFLAGS) $(INCLUDEDIRS) -o $@ -c $<
DO_CC=$(CC) $(CFLAGS) $(INCLUDEDIRS) -o $@ -c $<

#############################################################################
# SETUP AND BUILD
# GAME
#############################################################################

$(DLL_OBJDIR)/%.o: $(DLL_SRCDIR)/%.cpp
	$(DO_CXX)

$(GAME_SHARED_OBJDIR)/%.o: $(GAME_SHARED_SRCDIR)/%.cpp
	$(DO_CXX)

$(PM_SHARED_OBJDIR)/%.o: $(PM_SHARED_SRCDIR)/%.c
	$(DO_CC)

OBJ = \
	$(DLL_OBJDIR)/animating.o \
	$(DLL_OBJDIR)/animation.o \
	$(DLL_OBJDIR)/bmodels.o \
	$(DLL_OBJDIR)/buttons.o \
	$(DLL_OBJDIR)/cbase.o \
	$(DLL_OBJDIR)/client.o \
	$(DLL_OBJDIR)/combat.o \
	$(DLL_OBJDIR)/crossbow.o \
	$(DLL_OBJDIR)/crowbar.o \
	$(DLL_OBJDIR)/defaultai.o \
	$(DLL_OBJDIR)/doors.o \
	$(DLL_OBJDIR)/effects.o \
	$(DLL_OBJDIR)/egon.o \
	$(DLL_OBJDIR)/explode.o \
	$(DLL_OBJDIR)/func_break.o \
	$(DLL_OBJDIR)/func_tank.o \
	$(DLL_OBJDIR)/game.o \
	$(DLL_OBJDIR)/gamerules.o \
	$(DLL_OBJDIR)/gauss.o \
	$(DLL_OBJDIR)/genericmonster.o \
	$(DLL_OBJDIR)/ggrenade.o \
	$(DLL_OBJDIR)/globals.o \
	$(DLL_OBJDIR)/h_ai.o \
	$(DLL_OBJDIR)/h_battery.o \
	$(DLL_OBJDIR)/h_cycler.o \
	$(DLL_OBJDIR)/h_export.o \
	$(DLL_OBJDIR)/handgrenade.o \
	$(DLL_OBJDIR)/healthkit.o \
	$(DLL_OBJDIR)/hornet.o \
	$(DLL_OBJDIR)/hornetgun.o \
	$(DLL_OBJDIR)/items.o \
	$(DLL_OBJDIR)/lights.o \
	$(DLL_OBJDIR)/maprules.o \
	$(DLL_OBJDIR)/monsters.o \
	$(DLL_OBJDIR)/monsterstate.o \
	$(DLL_OBJDIR)/mortar.o \
	$(DLL_OBJDIR)/mp5.o \
	$(DLL_OBJDIR)/multiplay_gamerules.o \
	$(DLL_OBJDIR)/nodes.o \
	$(DLL_OBJDIR)/pathcorner.o \
	$(DLL_OBJDIR)/plane.o \
	$(DLL_OBJDIR)/plats.o \
	$(DLL_OBJDIR)/observer.o \
	$(DLL_OBJDIR)/player.o \
	$(DLL_OBJDIR)/python.o \
	$(DLL_OBJDIR)/rpg.o \
	$(DLL_OBJDIR)/satchel.o \
	$(DLL_OBJDIR)/schedule.o \
	$(DLL_OBJDIR)/scripted.o \
	$(DLL_OBJDIR)/shotgun.o \
	$(DLL_OBJDIR)/singleplay_gamerules.o \
	$(DLL_OBJDIR)/skill.o \
	$(DLL_OBJDIR)/sound.o \
	$(DLL_OBJDIR)/soundent.o \
	$(DLL_OBJDIR)/spectator.o \
	$(DLL_OBJDIR)/squadmonster.o \
	$(DLL_OBJDIR)/squeakgrenade.o \
	$(DLL_OBJDIR)/subs.o \
	$(DLL_OBJDIR)/talkmonster.o \
	$(DLL_OBJDIR)/triggers.o \
	$(DLL_OBJDIR)/tripmine.o \
	$(DLL_OBJDIR)/util.o \
	$(DLL_OBJDIR)/weapons.o \
	$(DLL_OBJDIR)/world.o \
	$(DLL_OBJDIR)/xen.o \
	$(DLL_OBJDIR)/glock.o \
	$(GAME_SHARED_OBJDIR)/voice_gamemgr.o \
	$(PM_SHARED_OBJDIR)/pm_debug.o \
	$(PM_SHARED_OBJDIR)/pm_math.o \
	$(PM_SHARED_OBJDIR)/pm_shared.o


$(DLLNAME) : neat $(OBJ)
	$(CXX) $(CFLAGS) $(LDFLAGS) -o $@ $(OBJ)

neat:
	-@mkdir -p $(DLL_OBJDIR)
	-@mkdir -p $(GAME_SHARED_OBJDIR)
	-@mkdir -p $(PM_SHARED_OBJDIR)
clean:
	-@rm -rf $(DLL_OBJDIR)
	-@rm -rf $(GAME_SHARED_OBJDIR)
	-@rm -rf $(PM_SHARED_OBJDIR)
	-@rm -rf $(DLLNAME)
