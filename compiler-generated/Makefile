ASM_EXT ?= .s
CCC ?= gcc -ggdb -pedantic-errors -std=c89 -Wall
IN_EXT ?= .c
OBJ_EXT ?= .o
OUT_EXT ?= .out
RUN ?= hello_world

INS := $(wildcard *$(IN_EXT))
OUTS_NOEXT := $(basename $(INS))
OUTS := $(addsuffix $(OUT_EXT), $(OUTS_NOEXT))

.PHONY: all clean run

all: $(OUTS)

%$(OUT_EXT): %$(IN_EXT)
	$(CCC) -S '$<' -o '$(basename $@)$(ASM_EXT)'
	$(CCC) -c '$(basename $@)$(ASM_EXT)' -o '$(basename $@)$(OBJ_EXT)'
	$(CCC) '$(basename $@)$(OBJ_EXT)' -o '$@'

clean:
	rm -f  *'$(ASM_EXT)' *'$(OBJ_EXT)' *'$(OUT_EXT)'

run: all
	./'$(RUN)$(OUT_EXT)'