# Makefile for NoMount

# NoMount is vendored into this kernel tree (fs/nomount/) from
# maxsteeel/nomount v2.3.1 (dcd77d03e991, rev-list 785), so there is no
# .git of its own. Pin the commit count upstream would compute.
NOMOUNT_COMMIT_COUNT ?= 785
ccflags-y += -DNOMOUNT_COMMIT_COUNT=\"$(NOMOUNT_COMMIT_COUNT)\"

obj-$(CONFIG_NOMOUNT) += nomount.o
ccflags-y += -std=gnu11 -Wno-declaration-after-statement -O3 -fno-stack-protector

ifeq ($(shell grep -qE '\(\*[[:space:]]*__get\)' $(srctree)/include/linux/xattr.h 2>/dev/null && echo 1 || echo 0),1)
ccflags-y += -DNM_HAS_XATTR__GET
endif
