# Assign some variables ONLY if they are not yet defined
FCP ?= gfortran
FFL ?= -c -O3 -mtune=native -march=native
BINDIR ?= ../bin

jac_anco.so : jac_anco.o
	gfortran -O3 -shared -fPIC -o $@ jac_anco.f90  rabs_anco.f90  rabs_angular.f90  rabs_constant.f90  rabs_csl.f90  \
		rabs_determinant.f90  rabs_dirac_orbital.f90  rabs_file_handling.f90  rabs_functions_math.f90  \
		rabs_functions_string.f90  rabs_grasp92.f90  rabs_io_dialog.f90  rabs_mcp_adaptation.f90  rabs_mcp_grasp92.f  \
		rabs_mcp_mct.f90  rabs_naglib.f90  rabs_njgraf.f  rabs_nucleus.f90  rabs_rcfp.f90  rabs_recoupling.f90 -o $(BINDIR)/libanco-ratip2013.so

.PHONY: clean

clean :
	$(RM) $(XEXE) *.o *.mod

%.o : %.f90
	$(FCP) $(FFL) $<

jac_anco.o :              rabs_anco.o  rabs_mcp_mct.o

rabs_anco.o :             rabs_angular.o  rabs_constant.o  rabs_csl.o  rabs_file_handling.o  rabs_rcfp.o  \
                          rabs_recoupling.o

rabs_angular.o :          rabs_constant.o  rabs_dirac_orbital.o  rabs_functions_math.o  rabs_io_dialog.o  rabs_naglib.o

rabs_constant.o :         

rabs_csl.o :              rabs_constant.o  rabs_determinant.o  rabs_dirac_orbital.o  rabs_functions_string.o

rabs_determinant.o :      rabs_constant.o  rabs_dirac_orbital.o

rabs_dirac_orbital.o :    rabs_constant.o  rabs_functions_math.o  rabs_naglib.o  rabs_nucleus.o

rabs_file_handling.o :    rabs_constant.o  rabs_csl.o  rabs_grasp92.o  rabs_io_dialog.o  rabs_nucleus.o

rabs_functions_math.o :   rabs_constant.o  rabs_naglib.o

rabs_functions_string.o : rabs_constant.o

rabs_grasp92.o :          rabs_constant.o  rabs_dirac_orbital.o  rabs_functions_math.o  rabs_nucleus.o

rabs_io_dialog.o :        rabs_constant.o  rabs_functions_math.o  rabs_functions_string.o  rabs_nucleus.o

rabs_mcp_adaptation.o :   rabs_angular.o  rabs_constant.o  rabs_dirac_orbital.o  rabs_mcp_mct.o

rabs_mcp_grasp92.o :      rabs_mcp_adaptation.o  rabs_njgraf.o

rabs_mcp_mct.o :          rabs_angular.o  rabs_constant.o  rabs_csl.o

rabs_naglib.o :           rabs_constant.o

rabs_njgraf.o :           

rabs_nucleus.o :          rabs_constant.o

rabs_rcfp.o :             rabs_angular.o  rabs_constant.o  rabs_functions_string.o

rabs_recoupling.o :       rabs_angular.o  rabs_constant.o  rabs_csl.o  rabs_rcfp.o
