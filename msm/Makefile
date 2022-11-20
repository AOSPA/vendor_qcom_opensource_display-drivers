# SPDX-License-Identifier: GPL-2.0

ifeq ($(ASUS_GKI_BUILD), y)
KBUILD_OPTIONS += ASUS_GKI_BUILD=y
endif

ifneq (,$(filter AI2201,$(ASUS_BUILD_PROJECT)))
KBUILD_OPTIONS += ASUS_AI2201_DISPLAY=y
endif

ifneq (,$(filter AI2202,$(ASUS_BUILD_PROJECT)))
KBUILD_OPTIONS += ASUS_AI2202_DISPLAY=y
endif

KBUILD_OPTIONS += DISPLAY_ROOT=$(KERNEL_SRC)/$(M)/../
KBUILD_OPTIONS += KBUILD_EXTRA_SYMBOLS=$(OUT_DIR)/../msm-modules/mmrm-driver/Module.symvers

all: modules

modules_install:
	$(MAKE) INSTALL_MOD_STRIP=1 -C $(KERNEL_SRC) M=$(M) modules_install

%:
	$(MAKE) -C $(KERNEL_SRC) M=$(M) $@ $(KBUILD_OPTIONS)

clean:
	rm -f *.o *.ko *.mod.c *.mod.o *~ .*.cmd Module.symvers
	rm -rf .tmp_versions

