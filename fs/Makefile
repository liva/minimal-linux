# SPDX-License-Identifier: GPL-2.0
#
# Makefile for the Linux filesystems.
#
# 14 Sep 2000, Christoph Hellwig <hch@infradead.org>
# Rewritten to use lists instead of if-statements.
# 

obj-y :=	open.o read_write.o file_table.o super.o \
		char_dev.o stat.o exec.o pipe.o namei.o fcntl.o \
		ioctl.o readdir.o select.o dcache.o inode.o \
		attr.o bad_inode.o file.o filesystems.o namespace.o \
		seq_file.o xattr.o libfs.o fs-writeback.o \
		pnode.o splice.o sync.o utimes.o \
		stack.o fs_struct.o statfs.o fs_pin.o nsfs.o

ifeq ($(CONFIG_BLOCK),y)
obj-y +=	buffer.o block_dev.o direct-io.o mpage.o
else
obj-y +=	no-block.o
endif

obj-$(CONFIG_PROC_FS) += proc_namespace.o

obj-$(CONFIG_ANON_INODES)	+= anon_inodes.o
obj-$(CONFIG_BINFMT_SCRIPT)	+= binfmt_script.o
obj-$(CONFIG_BINFMT_ELF)	+= binfmt_elf.o

obj-$(CONFIG_SYSCTL)		+= drop_caches.o

obj-$(CONFIG_PROC_FS)		+= proc/
obj-$(CONFIG_KERNFS)		+= kernfs/
obj-$(CONFIG_SYSFS)		+= sysfs/
obj-$(CONFIG_CONFIGFS_FS)	+= configfs/
obj-y				+= devpts/
obj-y				+= ramfs/

