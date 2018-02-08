# SPDX-License-Identifier: GPL-2.0
#
# Makefile for the linux memory manager.
#

KASAN_SANITIZE_slab_common.o := n
KASAN_SANITIZE_slab.o := n
KASAN_SANITIZE_slub.o := n

# These files are disabled because they produce non-interesting and/or
# flaky coverage that is not a function of syscall inputs. E.g. slab is out of
# free pages, or a task is migrated between nodes.
KCOV_INSTRUMENT_slab_common.o := n
KCOV_INSTRUMENT_slob.o := n
KCOV_INSTRUMENT_slab.o := n
KCOV_INSTRUMENT_slub.o := n
KCOV_INSTRUMENT_page_alloc.o := n
KCOV_INSTRUMENT_debug-pagealloc.o := n
KCOV_INSTRUMENT_kmemleak.o := n
KCOV_INSTRUMENT_memcontrol.o := n
KCOV_INSTRUMENT_mmzone.o := n
KCOV_INSTRUMENT_vmstat.o := n

mmu-y			:= nommu.o
mmu-$(CONFIG_MMU)	:= gup.o highmem.o memory.o mincore.o \
			   mlock.o mmap.o mprotect.o mremap.o msync.o \
			   page_vma_mapped.o pagewalk.o pgtable-generic.o \
			   rmap.o vmalloc.o


ifdef CONFIG_CROSS_MEMORY_ATTACH
mmu-$(CONFIG_MMU)	+= process_vm_access.o
endif

obj-y			:= filemap.o mempool.o oom_kill.o \
			   maccess.o page_alloc.o page-writeback.o \
			   readahead.o swap.o truncate.o vmscan.o shmem.o \
			   util.o mmzone.o vmstat.o backing-dev.o \
			   mm_init.o mmu_context.o percpu.o slab_common.o \
			   compaction.o vmacache.o swap_slots.o \
			   interval_tree.o list_lru.o workingset.o \
			   debug.o $(mmu-y)

obj-y += init-mm.o

obj-y		+= nobootmem.o

obj-$(CONFIG_HAVE_MEMBLOCK) += memblock.o

obj-$(CONFIG_HAS_DMA)	+= dmapool.o
obj-$(CONFIG_SPARSEMEM)	+= sparse.o
obj-$(CONFIG_SPARSEMEM_VMEMMAP) += sparse-vmemmap.o
obj-$(CONFIG_SLUB) += slub.o
obj-$(CONFIG_GENERIC_EARLY_IOREMAP) += early_ioremap.o
