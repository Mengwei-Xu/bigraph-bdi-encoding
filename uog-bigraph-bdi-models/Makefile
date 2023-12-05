# Sensible preable from https://tech.davis-hansson.com/p/make/
SHELL := bash
.SHELLFLAGS := -eu -o pipefail -c
.ONESHELL:
.DELETE_ON_ERROR:
MAKEFLAGS += --warn-undefined-variables
MAKEFLAGS += --no-builtin-rules

ifeq ($(origin .RECIPEPREFIX), undefined)
  $(error This Make does not support .RECIPEPREFIX. Please use GNU Make 4.0 or later)
endif
.RECIPEPREFIX = >

.PHONY : full sim clean prob

BIGRAPHER = ./bigrapher
MAX_STATES = 500
MAX_SIM = 500

full : bdi.big
> rm -f *.svg
> $(BIGRAPHER) full --solver=MiniCard -M $(MAX_STATES) -f svg -s . -t bdi.svg $<
> firefox bdi.svg

prob : bdi-probabilistic.big
> rm -f *.svg
> $(BIGRAPHER) full --solver=MiniCard -M $(MAX_STATES) -f svg -s . -t bdi.svg $<
> firefox bdi.svg

sim : bdi.big
> rm -f *.svg
> $(BIGRAPHER) sim --solver=MiniCARD -S $(MAX_SIM) -f svg -s . -t bdi_sim.svg $<
> firefox bdi_sim.svg

clean :
> rm -rf full/ sim/ *.svg *.dot
