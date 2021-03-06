#-------------------------------------------------------------------#
# High Power Rocketry - Avionics Hardware & Software
# MIT License
# Copyright (c) 2020 Roshan Doddanavar
# https://rdoddanavar.github.io
#  _   _                       _          _       
# | |_(_)_ _  ___ ___ __ ___ _(_)___ _ _ (_)__ ___
# | / / | ' \/ _ \___/ _` \ V / / _ \ ' \| / _(_-<
# |_\_\_|_||_\___/   \__,_|\_/|_\___/_||_|_\__/__/
#
# Path:
#     kino-avionics/software/kino_rpi/makefile
# Created:
#     2020-08-01
# Type:
#     Makefile
# Description:
#     Kino Raspberry Pi flight software - build script
# Dependencies:
#     <none>
#-------------------------------------------------------------------#

## PIGPIO NOTES:
# pigpio C build example:
# gcc -Wall -pthread -o foobar foobar.c -lpigpio -lrt
#
# -pthread Adds support for multithreading with the pthreads library.
# This option sets flags for both the preprocessor and linker.

## BUILD SETTINGS

# General
CC     = gcc
CFLAGS = -O3 -Wall -pthread 
LIBS   = -lpigpio -lrt
LIBDIR = ./pigpio
INCDIR = ./pigpio

# Kino RPI
EXEC = kino_rpi
SRC  = exec.c

## BUILD TARGETS

kino: $(SRC)
	$(CC) $(CFLAGS) -o $(EXEC) $(SRC) -I$(INCDIR) -L$(LIBDIR) -Wl,-rpath=$(LIBDIR) $(LIBS)

pigpio:
	make -C pigpio

all: pigpio kino

clean:
	rm -f $(EXEC) $(SRC:.c=.o)

all-clean:
	rm -f $(EXEC) $(SRC:.c=.o)
	make -C pigpio clean
