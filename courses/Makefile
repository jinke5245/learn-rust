# Simply by being mentioned as a target, this tells make to export all 
# variables to child processes by default. This is an alternative to using 
# export with no arguments. See Communicating Variables to a Sub-make.
.EXPORT_ALL_VARIABLES:

# If .NOTPARALLEL is mentioned as a target with no prerequisites, all targets 
# in this invocation of make will be run serially, even if the ‘-j’ option is 
# given. Any recursively invoked make command will still run recipes in parallel
# (unless its makefile also contains this target).
#
# If .NOTPARALLEL has targets as prerequisites, then all the prerequisites of 
# those targets will be run serially. This implicitly adds a .WAIT between each
# prerequisite of the listed targets. See Disabling Parallel Execution.
.NOTPARALLEL:

################################################################################
#
#  help targets
#
################################################################################

# Run `make help` to list available book targets.
help: ; @echo "make [ rust-book/book | rust-by-example/book ]"

# Use `make print-VARIABLE_NAME` to print the value of a specific variable.
print-%: ; @echo $($*)

################################################################################
#
#  book building targets
#
################################################################################

rust-book/js-extensions/node_modules:
	@cd rust-book/js-extensions && pnpm install --frozen-lockfile && pnpm build

rust-book/book: rust-book/js-extensions/node_modules
	@cd rust-book && mdbook build

rust-by-example/book:
	@cd rust-by-example && mdbook build
