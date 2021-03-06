#
#  Makefile
#  ARToolKit5
#
#  This file is part of ARToolKit.
#
#  ARToolKit is free software: you can redistribute it and/or modify
#  it under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation, either version 3 of the License, or
#  (at your option) any later version.
#
#  ARToolKit is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#  GNU Lesser General Public License for more details.
#
#  You should have received a copy of the GNU Lesser General Public License
#  along with ARToolKit.  If not, see <http://www.gnu.org/licenses/>.
#
#  As a special exception, the copyright holders of this library give you
#  permission to link this library with independent modules to produce an
#  executable, regardless of the license terms of these independent modules, and to
#  copy and distribute the resulting executable under terms of your choice,
#  provided that you also meet, for each linked independent module, the terms and
#  conditions of the license of that module. An independent module is a module
#  which is neither derived from nor based on this library. If you modify this
#  library, you may extend this exception to your version of the library, but you
#  are not obligated to do so. If you do not wish to do so, delete this exception
#  statement from your version.
#
#  Copyright 2015 Daqri, LLC.
#  Copyright 2002-2015 ARToolworks, Inc.
#
#  Author(s): Hirokazu Kato, Philip Lamb
#

UNAME = $(shell uname)

AR_HOME = ../../..
AR_CPPFLAGS = -I$(AR_HOME)/include

CC=gcc
CXX=g++ -std=c++11
CPPFLAGS = $(AR_CPPFLAGS)
CFLAGS = -O3 -fPIC -march=core2 -DHAVE_NFT=1
CXXFLAGS = -O3 -fPIC -march=core2 -DHAVE_NFT=1
AR=ar
ARFLAGS=rs
RANLIB = true

TARGET = $(AR_HOME)/lib/libAR.a

HEADERS = \
arLabelingSub/arLabelingPrivate.h \
arLabelingSub/arLabelingSub.h \
$(AR_HOME)/include/AR/ar.h \
$(AR_HOME)/include/AR/config.h \
$(AR_HOME)/include/AR/arConfig.h \
$(AR_HOME)/include/AR/matrix.h \
$(AR_HOME)/include/AR/icp.h \
$(AR_HOME)/include/AR/icpCore.h \
$(AR_HOME)/include/AR/matrix.h \
$(AR_HOME)/include/AR/param.h \
$(AR_HOME)/include/AR/arImageProc.h \
$(AR_HOME)/include/AR/arFilterTransMat.h \


OBJS = \
mAlloc.o \
mFree.o \
mAllocDup.o \
mDup.o \
mAllocTrans.o \
mTrans.o \
mAllocMul.o \
mMul.o \
mAllocInv.o \
mInv.o \
mSelfInv.o \
mAllocUnit.o \
mUnit.o \
mDisp.o \
mDet.o \
mPCA.o \
vAlloc.o \
vDisp.o \
vFree.o \
vHouse.o \
vInnerP.o \
vTridiag.o \
paramGetPerspective.o \
paramClear.o \
paramDecomp.o \
paramDistortion.o \
paramChangeSize.o \
paramFile.o \
paramLT.o \
paramDisp.o \
ar3DCreateHandle.o \
ar3DUtil.o \
arCreateHandle.o \
arDetectMarker.o \
arDetectMarker2.o \
arFilterTransMat.o \
arGetLine.o \
arGetMarkerInfo.o \
arGetTransMat.o \
arGetTransMatStereo.o \
arImageProc.o \
arLabeling.o \
arLabelingSub/arLabelingSubDBIC.o \
arLabelingSub/arLabelingSubDBRC.o \
arLabelingSub/arLabelingSubDBZ.o \
arLabelingSub/arLabelingSubDWIC.o \
arLabelingSub/arLabelingSubDWRC.o \
arLabelingSub/arLabelingSubDWZ.o \
arLabelingSub/arLabelingSubEBIC.o \
arLabelingSub/arLabelingSubEBRC.o \
arLabelingSub/arLabelingSubEBZ.o \
arLabelingSub/arLabelingSubEWIC.o \
arLabelingSub/arLabelingSubEWRC.o \
arLabelingSub/arLabelingSubEWZ.o \
arPattAttach.o \
arPattCreateHandle.o \
arPattGetID.o \
arPattLoad.o \
arPattSave.o \

ifneq "$(UNAME)" "Darwin"
OBJS += arUtil.o
endif

ifeq "$(UNAME)" "Darwin"
OBJS_OBJC = arUtil.o
endif


# Implicit rule, to compile C++ files with the .cpp suffix (rule already exists for .cc).
%.o : %.cpp
	$(CXX) -c $(CPPFLAGS) $(CXXFLAGS) $< -o $@

default build all: $(TARGET)

$(OBJS_OBJC): $(HEADERS)
	$(CC) $(CFLAGS) $(CPPFLAGS)  -c -ObjC -o $@ $*.c

$(OBJS): $(HEADERS)

$(TARGET): $(OBJS) $(OBJS_OBJC)
	$(AR) $(ARFLAGS) $@ $^
	$(RANLIB) $@

clean:
	-rm -f $(OBJS) $(OBJS_OBJC)
	-rm -f $(TARGET)

allclean:
	-rm -f $(OBJS) $(OBJS_OBJC)
	-rm -f $(TARGET)
	-rm -f Makefile

distclean:
	rm -f $(OBJS) $(OBJS_OBJC)
	rm -f Makefile

