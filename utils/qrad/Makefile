CC      := gcc
TARGET  := qrad

SRCS := \
	../common/bspfile.c \
	../common/cmdlib.c \
	lightmap.c \
	../common/mathlib.c \
	../common/polylib.c \
	qrad.c \
	../common/scriplib.c \
	../common/threads.c \
	trace.c \
	vismat.c

OBJS := $(SRCS:.c=.o)

CPPFLAGS := -I../common -DNDEBUG
CFLAGS   := -std=gnu89 -O3 -g -Wno-implicit-int -Wno-return-type -MMD -MP -ffloat-store -m32 -mfpmath=387 -march=pentium
LDFLAGS  := -m32
LDLIBS   := -lm -lpthread

all: $(TARGET)

$(TARGET): $(OBJS)
	$(CC) $(LDFLAGS) -o $@ $(OBJS) $(LDLIBS)

%.o: %.c
	$(CC) $(CPPFLAGS) $(CFLAGS) -c $< -o $@

clean:
	rm -f $(OBJS) $(OBJS:.o=.d) $(TARGET)

-include $(OBJS:.o=.d)
