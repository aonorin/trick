
#SYNOPSIS:
#
#   make [all]  - makes everything.
#   make TARGET - makes the given target.
#   make clean  - removes all files generated by make.

include ${TRICK_HOME}/share/trick/makefiles/Makefile.common

# Flags passed to the preprocessor.
TRICK_CPPFLAGS += -I$(GTEST_HOME)/include -I$(TRICK_HOME)/include -g -Wall -Wextra -DGTEST_HAS_TR1_TUPLE=0
 
TRICK_LIBS = -L${TRICK_LIB_DIR} -ltrick -ltrick_units -ltrick_mm
TRICK_EXEC_LINK_LIBS += ${GTEST_HOME}/lib/libgtest.a ${GTEST_HOME}/lib/libgtest_main.a

# All tests produced by this Makefile.  Remember to add new tests you
# created to the list.
TESTS = ITimer_test

OTHER_OBJECTS = ../../include/object_${TRICK_HOST_CPU}/io_JobData.o \
                ../../include/object_${TRICK_HOST_CPU}/io_SimObject.o

# House-keeping build targets.

all : $(TESTS)

test: $(TESTS)
	#./ITimer_test --gtest_output=xml:${TRICK_HOME}/trick_test/ITimer.xml

clean :
	rm -f $(TESTS) *.o

ITimer_test.o : ITimer_test.cpp
	$(TRICK_CPPC) $(TRICK_CPPFLAGS) -c $<

ITimer_test : ITimer_test.o
	$(TRICK_LD) $(TRICK_LDFLAGS) -o $@ $^ $(OTHER_OBJECTS) $(TRICK_LIBS) $(TRICK_LIBS) $(TRICK_EXEC_LINK_LIBS)

