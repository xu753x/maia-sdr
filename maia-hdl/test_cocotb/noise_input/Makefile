# defaults
SIM ?= icarus
TOPLEVEL_LANG ?= verilog

DUT = maia_sdr
# Force Verilog 2005 mode, since Verilog 2012 gives problems with initial value
# for combinatorial blocks.
VERILOG_SOURCES = -g2005
VERILOG_SOURCES += dut.v
VERILOG_SOURCES += tb.v
VERILOG_SOURCES += ../../XilinxUnisimLibrary/verilog/src/glbl.v
VERILOG_SOURCES += ../../XilinxUnisimLibrary/verilog/src/unisims/FIFO18E1.v
VERILOG_SOURCES += ../../XilinxUnisimLibrary/verilog/src/unisims/DSP48E1.v
TOPLEVEL = tb
MODULE = test_noise_input

COMPILE_ARGS += -Wall

export PYTHONPATH := $(PWD)/../..:$(PYTHONPATH)

# include cocotb's make rules to take care of the simulator setup
include $(shell cocotb-config --makefiles)/Makefile.sim

.PHONY: dut.v
dut.v:
	python3 verilog.py

.PHONY: -g2005
-g2005:
	echo "Verilog 2005 mode enabled"
