#EOC
#------------------------------------------------------------------------------
#          Harvard University Atmospheric Chemistry Modeling Group            !
#------------------------------------------------------------------------------
#BOP
#
# !MODULE: GNUmakefile
#
# !DESCRIPTION: This is the main makefile that will automatically build and 
#  install the following libraries on your system:
#
#  \begin{enumerate}
#  \item ZLIB (i.e. gzip/gunzip) version 1.2.6
#  \item HDF5 version 1.8.8
#  \item netCDF C/C++ libraries version 4.2
#  \item netCDF F77/F90 libraries version 4.2
#  \end{enumerate}
#
#  We recommend that you build the full netCDF-4.2 libraries, as this is the 
#  most recent library version.  You also have the option to build the 
#  netCDF "classic" library, which lacks the full functionality of netCDF-4.
#\\
#\\
# !REMARKS:
#  CALLING SEQUENCE TO BUILD netCDF-4:
#  ----------------------------------------------------------------------------
#  To build the netCDF-4 library (and related libraries) using the Intel
#  Fortran Compiler ("IFORT"), type:
#                                                                             .
#     make PREFIX=root_library_dir [GCC=yes]
#                                                                             .
#  To build the libraries for the PGI compiler, type:
#                                                                             .
#     make COMPILER=pgi PREFIX=root_library_dir [GCC=yes]
#                                                                             .
#  Where "root_library_dir" is the full path of the directory where 
#  you would like to install the libraries.  If you have sysadmin privileges, 
#  then you can install the libraries directly into /usr/opt /usr/local,
#  or whatever is the customary library path on your machine. 
#                                                                             .
#  If you do not have sysadmin privileges, then you can install the libraries
#  on a directory in your home space, such as /home/YOUR_USER_ID/lib.
#                                                                             .
#  If you do not select a value for PREFIX, then the default values of
#  "root_library_dir" will be assigned:
#                                                                             .
#     For IFORT compiler:  root_library_dir = "../opt/ifort/nc4"
#     For PGI   compiler:  root_library_dir = "../opt/pgi/nc4"
#                                                                             .
#  You can install the libraries into the default "root_library_dir" path
#  and then have your sysadmin move them to a common space on your machine.
#                                                                             .
#  Individual library files will be installed into various subdirectories
#  of "root_library_dir", as follows:
#                                                                             .
#     root_library_dir/bin            # nc-config, ncdump, ncgen, etc.
#     root_library_dir/include        # Include files (*.h)
#     root_library_dir/lib            # Library files (libz.a)
#     root_library_dir/share          # Manual pages & documentation
#                                                                             .
#  Finally, if you do not have the Intel C/C++ compilers or PGI C/C++ 
#  compilers installed on your system, using the GCC=yes option will tell 
#  the installer to use the GNU C/C++ compilers (gcc, g++) instead. 
#                                                                             .
#                                                                             .
#  CALLING SEQUENCE TO BUILD "netCDF CLASSIC"
#  ----------------------------------------------------------------------------
#  To build the "classic" netCDF libraries (which lack the advanced features
#  of netCDF-4) type:
#                                                                             .
#     make CLASSIC=yes PREFIX=root_library_dir [GCC=yes]
#                                                                             .
#  To build the libraries for the PGI compiler, type:
#                                                                             .
#     make CLASSIC=yes COMPILER=pgi PREFIX=root_library_dir [GCC=yes]
#                                                                             .
#  Where "root_library_dir" is the full path of the directory where 
#  you would like to install the libraries.  If you have sysadmin privileges, 
#  then you can install the libraries directly into /usr/opt /usr/local,
#  or whatever is the customary library path on your machine. 
#                                                                             .
#  If you do not have sysadmin privileges, then you can install the libraries
#  on a directory in your home space, such as /home/YOUR_USER_ID/lib.
#                                                                             .
#  If you do not select a value for PREFIX, then the default values of
#  "root_library_dir" will be assigned:
#                                                                             .
#     For IFORT compiler:  root_library_dir = "../opt/ifort/nc_classic"
#     For PGI   compiler:  root_library_dir = "../opt/pgi/nc_classic"
#                                                                             .
#  You can install the libraries into the default "root_library_dir" path
#  and then have your sysadmin move them to a common space on your machine.
#                                                                             .
#  Individual library files will be installed into various subdirectories
#  of "root_library_dir", as follows:
#                                                                             .
#     root_library_dir/bin            # nc-config, ncdump, ncgen, etc.
#     root_library_dir/include        # Include files (*.h)
#     root_library_dir/lib            # Library files (*.a)
#     root_library_dir/share          # Manual pages & documentation
#
#  Finally, if you do not have the Intel C/C++ compilers or PGI C/C++ 
#  compilers installed on your system, using the GCC=yes option will tell 
#  the installer to use the GNU C/C++ compilers (gcc, g++) instead. 
#                                                                             .
#                                                                             .
#  TELLING GEOS-CHEM WHERE TO FIND THE LIBRARIES:
#  ----------------------------------------------------------------------------
#  GEOS-Chem will rely on certain environment variables to tell it where to
#  find the various libraries.  These environment variables may be placed
#  in your .cshrc or .bashrc file, depending on which shell you use.
#                                                                             .
#     If you use "csh" or "tcsh", add this to your .cshrc file:
#     --------------------------------------------------------------------
#     setenv ROOT_LIBRARY_DIR same directory as root_library_dir above
#     setenv GC_BIN           $ROOT_LIBRARY_DIR/bin
#     setenv GC_INCLUDE       $ROOT_LIBRARY_DIR/include
#     setenv GC_LIB           $ROOT_LIBRARY_DIR/lib 
#                                                                             .
#     Then type "source ~/.cshrc" at the Unix prompt to accept the changes.
#                                                                             .
#                                                                             .
#     If you use "sh",   add this to your .profile file:
#     If you use "bash", add this to your .bashrc  file:
#     --------------------------------------------------------------------
#     ROOT_LIBRARY_DIR=same directory as root_library_dir above
#     GC_BIN=$ROOT_LIBRARY_DIR/bin
#     GC_INCLUDE=$ROOT_LIBRARY_DIR/include
#     GC_LIB=$ROOT_LIBRARY_DIR/lib
#     export GC_BIN
#     export GC_INCLUDE
#     export GC_LIB
#                                                                             .
#     Then type "source ~/.profile" (for sh) 
#     or        "source ~/.bashrc"  (for bash)
#     to accept the changes.
#
# !REVISION HISTORY: 
#  26 Apr 2012 - R. Yantosca - Initial version, based on NASA Baselibs
#  27 Apr 2012 - R. Yantosca - Now do not build ZLIB for netCDF-3
#  27 Apr 2012 - R. Yantosca - Better test for default value for $(PREFIX)
#  27 Apr 2012 - R. Yantosca - Added extra documentation
#  02 May 2012 - R. Yantosca - Added "display" target for printing variables
#  02 May 2012 - R. Yantosca - Updated to netCDF-4.2
#  08 May 2012 - R. Yantosca - FINALLY works with netcdf-fortran-4.2!!!
#  10 May 2012 - R. Yantosca - Updated comments about GC environment variables
#  11 May 2012 - R. Yantosca - Fixed errors in comments
#  11 May 2012 - R. Yantosca - Add GCC variable to use gcc/g++ compilers
#                              instead of icc/icpc and pgcc, pgcpp compilers
#  06 Oct 2014 - R. Yantosca - Updated netCDF libraries to netcdf-4.3.2 and
#                              netcdf-fortran-4.1.1 for newer Linux builds
#  23 Oct 2014 - R. Yantosca - Updated to HDF-1.8.9
#  23 Oct 2014 - R. Yantosca - Now use regexp for yes/no questions (GCC=yes)
#  24 Oct 2014 - R. Yantosca - Now enable parallel netCDF
#EOP
#------------------------------------------------------------------------------
#BOC

#==============================================================================
# Default settings for Makefile options
#==============================================================================

# Default shell
SHELL            := /bin/bash

# Code directories 
CODE_ZLIB        := zlib-1.2.6
CODE_HDF5        := hdf5-1.8.9
CODE_NC4         := netcdf-4.3.2
CODE_NC4_F90     := netcdf-fortran-4.4.1
DOC              := doc

# IFORT is default compiler
ifndef COMPILER
 COMPILER        := ifort
endif

# Use the GNU C compilers instead of Intel/PGI compilers
ifndef GCC
 GCC             := no
endif

# Determine if we want to build netCDF-4 or netCDF-CLASSIC
ifndef CLASSIC
 CLASSIC         := no
endif

# If CLASSIC=yes, then we'll build the netCDF classic library
# Otherwise, we'll build the full netCDF-4.2 library
ifeq ($(CLASSIC),yes)
 DEFAULT_TARGET  := nc_classic verify
 PREF_DIR        := nc_classic
else
 DEFAULT_TARGET  := zlib hdf5 nc4 verify
 PREF_DIR        := nc4
endif

# Default dir where library files will be created
# This should be in GEOS-Chem-Libraries/opt/$(COMPILER)
ifndef PREFIX
 PREFIX          := $(PWD)
 ifeq ($(findstring src,$(PREFIX)),src)
  PREFIX         := $(PREFIX)/../opt/$(COMPILER)/$(PREF_DIR)
 else
  PREFIX         := $(PREFIX)/opt/$(COMPILER)/$(PREF_DIR)
 endif  
endif

# Output directories for each library build
PREFIX_ZLIB      := $(PREFIX)
PREFIX_HDF5      := $(PREFIX)
PREFIX_DOXY      := $(PREFIX)
PREFIX_NC4       := $(PREFIX)

# Settings for IFORT compilers
ifeq ($(COMPILER),ifort) 
 FC              := ifort
 F90             := ifort
 F77             := ifort
 REGEXP          :=(^[Yy]|^[Yy][Ee][Ss])
 ifeq ($(shell [[ "$(GCC)" =~ $(REGEXP) ]] && echo true),true)
  CC             := gcc
  CXX            := g++
  NCDF_F90_FLAG  :="--disable-fortran-type-check"
 else
  CC             := icc
  CXX            := icpc
  NCDF_F90_FLAG  :=""
 endif
 CPP             := "$(CC) -c -E"
 FFLAGS          := "-fpic -mcmodel=medium"
 FCFLAGS         := "-fpic -mcmodel=medium"
 CFLAGS          := "-fpic -mcmodel=medium"
 CXXFLAGS        := "-fpic -mcmodel=medium"
 CPPFLAGS        := -I$(PREFIX)/include
 LDFLAGS         := -L$(PREFIX)/lib
 LD_LIBRARY_PATH := $(PREFIX)/lib:$(LD_LIBRARY_PATH)
endif

# Settings for PGI compilers
ifeq ($(COMPILER),pgi) 
 FC              := pgf90
 F90             := pgf90
 F77             := pgf90
 REGEXP          :=(^[Yy]|^[Yy][Ee][Ss])
 ifeq ($(shell [[ "$(GCC)" =~ $(REGEXP) ]] && echo true),true)
  CC             := gcc
  CXX            := g++
  NCDF_F90_FLAG  :="--disable-fortran-type-check"
 else
  CC             := pgcc
  CXX            := pgcpp
  NCDF_F90_FLAG  :=""
 endif
 CPP             := "$(CC) -c -E"
 FFLAGS          := "-fpic -mcmodel=medium"
 FCFLAGS         := "-fpic -mcmodel=medium"
 CFLAGS          := "-fpic -mcmodel=medium"
 CXXFLAGS        := "-fpic -mcmodel=medium"
 CPPFLAGS        := -I$(PREFIX)/include          
 LDFLAGS         := -L$(PREFIX)/lib              
 LD_LIBRARY_PATH := $(PREFIX)/lib:$(LD_LIBRARY_PATH)
endif

# Export the linker library
export LD_LIBRARY_PATH

#==============================================================================
# Makefile targets
#==============================================================================

.PHONY: all doc verify

all: $(DEFAULT_TARGET)

zlib:
	if [ -f $(CODE_ZLIB)/$(CODE_ZLIB).install ] ; then                    \
	   echo '====> ZLIB has already been installed!';                     \
	else                                                                  \
	   cd $(CODE_ZLIB)                                                  &&\
	   ./configure --prefix=$(PREFIX_ZLIB) --static --64                &&\
	   touch $(CODE_ZLIB).config                                        &&\
	   $(MAKE) check                                                    &&\
	   $(MAKE) install                                                  &&\
	   touch $(CODE_ZLIB).install                                       &&\
	   echo '====> ZLIB was installed successfully!';                     \
	fi                                                                   

hdf5:
	if [ -f $(CODE_HDF5)/$(CODE_HDF5).install ] ; then                    \
	   echo '====> HDF5 has already been installed';                      \
	else                                                                  \
	   if [ -f $(CODE_ZLIB)/$(CODE_ZLIB).install ] ; then                 \
	      cd $(CODE_HDF5)                                               &&\
	      ./configure                                                     \
                 --prefix=$(PREFIX_HDF5)                                      \
                 --disable-shared                                             \
                 --with-zlib=$(PREFIX_ZLIB)                                   \
	         FC=$(FC)      FCFLAGS=$(FCFLAGS)                             \
	         CC=$(CC)      CFLAGS=$(CFLAGS)                               \
	         CXX=$(CXX)    CXXFLAGS=$(CPPFLAGS)                           \
	         CPP=$(CPP)    LDFLAGS=$(LDFLAGS)                           &&\
	      touch $(CODE_HDF5).config                                     &&\
	      $(MAKE)                                                       &&\
	      $(MAKE) install                                               &&\
	      touch $(CODE_HDF5).install                                    &&\
	      echo '====> HDF5 was installed successfully!';                  \
	   else                                                               \
	      echo '====> ERROR: ZLIB has not been installed!';               \
	      exit;                                                           \
	   fi;                                                                \
	fi

nc4:
	if [ -f $(CODE_NC4_F90)/$(CODE_NC4_F90).install ] ; then              \
	   echo '====> NETCDF-4 has already been installed!';                 \
	else                                                                  \
	   if [ -f $(CODE_HDF5)/$(CODE_HDF5).install ] ; then                 \
	      cd $(CODE_NC4)                                                &&\
	      ./configure                                                     \
                          --prefix=$(PREFIX_NC4)                              \
	                  --disable-shared                                    \
	                  --disable-doxygen                                   \
	                  CC=$(CC)      CFLAGS=$(CFLAGS)                      \
	                  CPP=$(CPP)    CPPFLAGS=$(CPPFLAGS)                  \
	                  LIBS=$(LIBS)  LDFLAGS=$(LDFLAGS)                  &&\
	      touch $(CODE_NC4).config                                      &&\
	      $(MAKE) check                                                 &&\
	      $(MAKE) install                                               &&\
	      touch $(CODE_NC4).install                                     &&\
	      cd ../$(CODE_NC4_F90)                                         &&\
	      lt_cv_ld_force_load=no                                        &&\
	      LD_LIBRARY_PATH=$(LD_LIBRARY_PATH)                            &&\
              ./configure --prefix=$(PREFIX_NC4)                              \
	                  --disable-shared                                    \
                          $(NCDF_F90_FLAG)                                    \
	                  F77=$(F77)       FFLAGS=$(FFLAGS)                   \
	                  FC=$(FC)         FCFLAGS=$(FCFLAGS)                 \
	                  CC=$(CC)         CFLAGS="$(CFLAGS) -D$(FC)"         \
	                  CPP=$(CPP)       CPPFLAGS=$(CPPFLAGS)               \
	                  LIBS="-lnetcdf"  LDFLAGS=$(LDFLAGS)               &&\
	      touch $(CODE_NC4_F90).config                                  &&\
	      $(MAKE) check                                                 &&\
	      $(MAKE) install                                               &&\
	      touch $(CODE_NC4_F90).install                                 &&\
	      echo '====> NETCDF-4 has been installed successfully!';         \
	   else                                                               \
	      echo '====> ERROR: HDF5 has not been installed!';               \
	      exit;                                                           \
	   fi;                                                                \
	fi;

nc_classic:
	if [ -f $(CODE_NC4_F90)/$(CODE_NC4_F90).install.classic ] ; then      \
	   echo '====> NETCDF CLASSIC has already been installed!';           \
	else                                                                  \
	   cd $(CODE_NC4)                                                   &&\
	   ./configure --prefix=$(PREFIX_NC4)                                 \
                       --disable-shared                                       \
	               --disable-netcdf-4                                     \
	               --disable-doxygen                                      \
	               --disable-dap                                          \
	                 CC=$(CC)      CFLAGS=$(CFLAGS)                       \
	                 CPP=$(CPP)    CPPFLAGS=$(CPPFLAGS)                   \
	                 LIBS=$(LIBS)  LDFLAGS=$(LDFLAGS)                   &&\
	   touch $(CODE_NC4).config.classic                                 &&\
           $(MAKE) check                                                    &&\
           $(MAKE) install                                                  &&\
           touch $(CODE_NC4).install.classic                                &&\
	   cd ../$(CODE_NC4_F90)                                            &&\
	   lt_cv_ld_force_load=no                                           &&\
	   LD_LIBRARY_PATH=$(LD_LIBRARY_PATH)                               &&\
	   ./configure --prefix=$(PREFIX_NC4)                                 \
                       --disable-shared                                       \
	               --disable-netcdf-4                                     \
                       $(NCDF_F90_FLAG)                                       \
	               F77=$(F77)       FFLAGS=$(FFLAGS)                      \
	               FC=$(FC)         FCFLAGS=$(FCFLAGS)                    \
	               CC=$(CC)         CFLAGS="$(CFLAGS) -D($FC)"            \
	               CPP=$(CPP)       CPPFLAGS=$(CPPFLAGS)                  \
	               LIBS="-lnetcdf"  LDFLAGS=$(LDFLAGS)                  &&\
	   touch $(CODE_NC4_F90).config.classic                             &&\
	   $(MAKE) check                                                    &&\
	   $(MAKE) install                                                  &&\
	   touch $(CODE_NC4_F90).install.classic                            &&\
	   echo '====> NETCDF CLASSIC has been installed successfully!';      \
	fi;

verify:
	@ argv="$(CODE_ZLIB) $(CODE_HDF5) $(CODE_NC4) $(CODE_NC4_F90)";       \
        ( echo "-------+---------+-------------------------------------" );   \
        ( echo "Config | Install |             Package"                 );    \
        ( echo "-------+---------+-------------------------------------" );   \
	for d in $$argv; do        			                      \
          if [ -f $$d/$$d.config ] ; then                                     \
             cfg='  ok  ';                                                    \
	     cls='';                                                          \
          else                                                                \
	     if [ -f $$d/$$d.config.classic ] ; then                          \
                cfg='  ok  ';                                                 \
	        cls='(netCDF classic)';                                       \
	     else                                                             \
                cfg='  --  ';                                                 \
	     fi;                                                              \
          fi;                                                                 \
          if [ -f $$d/$$d.install ] ; then                                    \
             inst='  ok   ';                                                  \
	     cls='';                                                          \
          else                                                                \
	     if [ -f $$d/$$d.install.classic ] ; then                         \
                inst='  ok   ';                                               \
	        cls='(netCDF classic)';                                       \
	     else                                                             \
                inst='  --   ';                                               \
	     fi;                                                              \
          fi;                                                                 \
          ( echo "$$cfg | $$inst | $$d $$cls" );                              \
	done ;                                                                \
        ( echo "-------+---------+-------------------------------------" )

doc:
	@$(MAKE) -C $(DOC) all

clean_doc:
	@$(MAKE) -C $(DOC) clean

clean_zlib:
	rm -f $(CODE_ZLIB)/$(CODE_ZLIB).config
	rm -f $(CODE_ZLIB)/$(CODE_ZLIB).install
	@$(MAKE) -C $(CODE_ZLIB) clean

clean_hdf5:
	rm -f $(CODE_HDF5)/$(CODE_HDF5).config
	rm -f $(CODE_HDF5)/$(CODE_HDF5).install
	@$(MAKE) -C $(CODE_HDF5) clean

clean_netcdf clean_nc4:
	rm -f $(CODE_NC4)/$(CODE_NC4).config*
	rm -f $(CODE_NC4)/$(CODE_NC4).install*
	rm -f $(CODE_NC4_F90)/$(CODE_NC4_F90).config*
	rm -f $(CODE_NC4_F90)/$(CODE_NC4_F90).install*
	@$(MAKE) -C $(CODE_NC4)     clean
	@$(MAKE) -C $(CODE_NC4_F90) clean

distclean:
	rm -rf $(PREFIX_ZLIB)
	rm -rf $(PREFIX_HDF5)
	rm -rf $(PREFIX_DOXY)
	rm -rf $(PREFIX_NC4)
	@$(MAKE) clean_doc
	@$(MAKE) clean_nc4
	@$(MAKE) -C $(CODE_NC4)     distclean
	@$(MAKE) -C $(CODE_NC4_F90) distclean
	if [ ! -f $(CLASSIC) == "yes" ] ; then                                \
	   @$(MAKE) clean_zlib;                                               \
	   @$(MAKE) clean_hdf5;                                               \
	   @$(MAKE) -C $(CODE_ZLIB) distclean;                                \
	   @$(MAKE) -C $(CODE_HDF5) distclean;                                \
	fi

#==============================================================================
# Makefile targets
#==============================================================================

help:
	@echo '%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%'
	@echo '%%%     GEOS-Chem-Libraries help screen     %%%'
	@echo '%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%'
	@echo
	@echo 'Usage: make                # Builds netCDF-4 library'
	@echo '       make CLASSIC=yes    # Builds netCDF classic library'
	@echo ''
	@echo 'You may also use one of these optional targets'
	@echo 'help            Displays this help screen'
	@echo 'verify          Verifies that libraries have been installed'
	@echo 'doc             Builds documentation in src/doc/ subdirectory' 
	@echo 'clean_doc       Removes documentation from src/doc subdirectory'
	@echo 'clean_zlib      Cleans up ZLIB code'
	@echo 'clean_hdf5      Cleans up HDF5 code'
	@echo 'clean_netcdf    Cleans up netCDF code'
	@echo 'distclean       Removes all libraries and builds clean'
	@echo ''
	@echo 'OPTIONAL-FLAGS may be:'
	@echo 'COMPILER=___   Options: ifort pgi default is ifort)'
	@echo 'PREFIX=path    Specifies root path for library installation'

#EOC
