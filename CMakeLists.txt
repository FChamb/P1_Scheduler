cmake_minimum_required(VERSION 3.27)
project(P1_Scheduler)

set(CMAKE_CXX_STANDARD 14)

include_directories(stacsos/kernel/inc)
include_directories(stacsos/kernel/inc/stacsos)
include_directories(stacsos/kernel/inc/stacsos/kernel)
include_directories(stacsos/kernel/inc/stacsos/kernel/arch)
include_directories(stacsos/kernel/inc/stacsos/kernel/arch/x86)
include_directories(stacsos/kernel/inc/stacsos/kernel/arch/x86/boot)
include_directories(stacsos/kernel/inc/stacsos/kernel/arch/x86/irq)
include_directories(stacsos/kernel/inc/stacsos/kernel/dev)
include_directories(stacsos/kernel/inc/stacsos/kernel/dev/acpi)
include_directories(stacsos/kernel/inc/stacsos/kernel/dev/console)
include_directories(stacsos/kernel/inc/stacsos/kernel/dev/gfx)
include_directories(stacsos/kernel/inc/stacsos/kernel/dev/input)
include_directories(stacsos/kernel/inc/stacsos/kernel/dev/misc)
include_directories(stacsos/kernel/inc/stacsos/kernel/dev/pci)
include_directories(stacsos/kernel/inc/stacsos/kernel/dev/storage)
include_directories(stacsos/kernel/inc/stacsos/kernel/dev/timers)
include_directories(stacsos/kernel/inc/stacsos/kernel/dev/tty)
include_directories(stacsos/kernel/inc/stacsos/kernel/fs)
include_directories(stacsos/kernel/inc/stacsos/kernel/mem)
include_directories(stacsos/kernel/inc/stacsos/kernel/obj)
include_directories(stacsos/kernel/inc/stacsos/kernel/sched)
include_directories(stacsos/kernel/inc/stacsos/kernel/sched/alg)
include_directories(stacsos/lib/inc)
include_directories(stacsos/lib/inc/stacsos)
include_directories(stacsos/user/ulib/inc)
include_directories(stacsos/user/ulib/inc/stacsos)

add_executable(P1_Scheduler
        stacsos/kernel/inc/stacsos/kernel/arch/x86/boot/multiboot.h
        stacsos/kernel/inc/stacsos/kernel/arch/x86/irq/irq-manager.h
        stacsos/kernel/inc/stacsos/kernel/arch/x86/irq/irq-traps.h
        stacsos/kernel/inc/stacsos/kernel/arch/x86/cpuid-features.h
        stacsos/kernel/inc/stacsos/kernel/arch/x86/cpuid.h
        stacsos/kernel/inc/stacsos/kernel/arch/x86/cregs.h
        stacsos/kernel/inc/stacsos/kernel/arch/x86/dt.h
        stacsos/kernel/inc/stacsos/kernel/arch/x86/ioapic.h
        stacsos/kernel/inc/stacsos/kernel/arch/x86/machine-context.h
        stacsos/kernel/inc/stacsos/kernel/arch/x86/msr.h
        stacsos/kernel/inc/stacsos/kernel/arch/x86/page-table-structures.h
        stacsos/kernel/inc/stacsos/kernel/arch/x86/pio.h
        stacsos/kernel/inc/stacsos/kernel/arch/x86/pit.h
        stacsos/kernel/inc/stacsos/kernel/arch/x86/text-console.h
        stacsos/kernel/inc/stacsos/kernel/arch/x86/tsc.h
        stacsos/kernel/inc/stacsos/kernel/arch/x86/x2apic-structures.h
        stacsos/kernel/inc/stacsos/kernel/arch/x86/x2apic-timer.h
        stacsos/kernel/inc/stacsos/kernel/arch/x86/x2apic.h
        stacsos/kernel/inc/stacsos/kernel/arch/x86/x86-core.h
        stacsos/kernel/inc/stacsos/kernel/arch/x86/x86-page-table.h
        stacsos/kernel/inc/stacsos/kernel/arch/x86/x86-platform.h
        stacsos/kernel/inc/stacsos/kernel/arch/console-interface.h
        stacsos/kernel/inc/stacsos/kernel/arch/core-manager.h
        stacsos/kernel/inc/stacsos/kernel/arch/core.h
        stacsos/kernel/inc/stacsos/kernel/arch/irq-manager.h
        stacsos/kernel/inc/stacsos/kernel/arch/irq.h
        stacsos/kernel/inc/stacsos/kernel/arch/platform.h
        stacsos/kernel/inc/stacsos/kernel/arch/timer.h
        stacsos/kernel/inc/stacsos/kernel/dev/acpi/acpi.h
        stacsos/kernel/inc/stacsos/kernel/dev/acpi/descriptors.h
        stacsos/kernel/inc/stacsos/kernel/dev/console/physical-console.h
        stacsos/kernel/inc/stacsos/kernel/dev/console/virtual-console.h
        stacsos/kernel/inc/stacsos/kernel/dev/gfx/graphics.h
        stacsos/kernel/inc/stacsos/kernel/dev/gfx/qemu-stdvga.h
        stacsos/kernel/inc/stacsos/kernel/dev/input/keyboard.h
        stacsos/kernel/inc/stacsos/kernel/dev/input/keys.h
        stacsos/kernel/inc/stacsos/kernel/dev/misc/cmos-rtc.h
        stacsos/kernel/inc/stacsos/kernel/dev/misc/rtc.h
        stacsos/kernel/inc/stacsos/kernel/dev/pci/pci-device-config.h
        stacsos/kernel/inc/stacsos/kernel/dev/pci/pci-device.h
        stacsos/kernel/inc/stacsos/kernel/dev/pci/pci-express-bus.h
        stacsos/kernel/inc/stacsos/kernel/dev/storage/ahci-controller.h
        stacsos/kernel/inc/stacsos/kernel/dev/storage/ahci-storage-device.h
        stacsos/kernel/inc/stacsos/kernel/dev/storage/ahci-structures.h
        stacsos/kernel/inc/stacsos/kernel/dev/storage/block-device.h
        stacsos/kernel/inc/stacsos/kernel/dev/timers/pit.h
        stacsos/kernel/inc/stacsos/kernel/dev/timers/timer.h
        stacsos/kernel/inc/stacsos/kernel/dev/tty/terminal.h
        stacsos/kernel/inc/stacsos/kernel/dev/bus.h
        stacsos/kernel/inc/stacsos/kernel/dev/devfs.h
        stacsos/kernel/inc/stacsos/kernel/dev/device-class.h
        stacsos/kernel/inc/stacsos/kernel/dev/device-manager.h
        stacsos/kernel/inc/stacsos/kernel/dev/device.h
        stacsos/kernel/inc/stacsos/kernel/fs/file.h
        stacsos/kernel/inc/stacsos/kernel/fs/filesystem.h
        stacsos/kernel/inc/stacsos/kernel/fs/fs-node.h
        stacsos/kernel/inc/stacsos/kernel/fs/tar-filesystem.h
        stacsos/kernel/inc/stacsos/kernel/fs/vfs.h
        stacsos/kernel/inc/stacsos/kernel/mem/address-space-region.h
        stacsos/kernel/inc/stacsos/kernel/mem/address-space.h
        stacsos/kernel/inc/stacsos/kernel/mem/large-object-allocator.h
        stacsos/kernel/inc/stacsos/kernel/mem/memory-manager.h
        stacsos/kernel/inc/stacsos/kernel/mem/object-allocator.h
        stacsos/kernel/inc/stacsos/kernel/mem/page-alloc-ref.h
        stacsos/kernel/inc/stacsos/kernel/mem/page-allocator-buddy.h
        stacsos/kernel/inc/stacsos/kernel/mem/page-allocator-linear.h
        stacsos/kernel/inc/stacsos/kernel/mem/page-allocator.h
        stacsos/kernel/inc/stacsos/kernel/mem/page-table-allocator.h
        stacsos/kernel/inc/stacsos/kernel/mem/page-table.h
        stacsos/kernel/inc/stacsos/kernel/mem/page.h
        stacsos/kernel/inc/stacsos/kernel/mem/slab-cache.h
        stacsos/kernel/inc/stacsos/kernel/obj/object-manager.h
        stacsos/kernel/inc/stacsos/kernel/obj/object.h
        stacsos/kernel/inc/stacsos/kernel/sched/alg/priority.h
        stacsos/kernel/inc/stacsos/kernel/sched/alg/rr.h
        stacsos/kernel/inc/stacsos/kernel/sched/alg/scheduling-algorithm.h
        stacsos/kernel/inc/stacsos/kernel/sched/alg/sfs.h
        stacsos/kernel/inc/stacsos/kernel/sched/event.h
        stacsos/kernel/inc/stacsos/kernel/sched/process-manager.h
        stacsos/kernel/inc/stacsos/kernel/sched/process.h
        stacsos/kernel/inc/stacsos/kernel/sched/schedulable-entity.h
        stacsos/kernel/inc/stacsos/kernel/sched/scheduler.h
        stacsos/kernel/inc/stacsos/kernel/sched/sleeper.h
        stacsos/kernel/inc/stacsos/kernel/sched/thread.h
        stacsos/kernel/inc/stacsos/kernel/config.h
        stacsos/kernel/inc/stacsos/kernel/debug.h
        stacsos/kernel/inc/stacsos/kernel/kernel-global.h
        stacsos/kernel/inc/stacsos/kernel/lock.h
        stacsos/kernel/src/arch/x86/boot/start.cpp
        stacsos/kernel/src/arch/x86/irq/irq-manager.cpp
        stacsos/kernel/src/arch/x86/bsod.cpp
        stacsos/kernel/src/arch/x86/cpuid.cpp
        stacsos/kernel/src/arch/x86/dt.cpp
        stacsos/kernel/src/arch/x86/ioapic.cpp
        stacsos/kernel/src/arch/x86/machine-context.cpp
        stacsos/kernel/src/arch/x86/pit.cpp
        stacsos/kernel/src/arch/x86/text-console.cpp
        stacsos/kernel/src/arch/x86/tsc.cpp
        stacsos/kernel/src/arch/x86/x2apic-timer.cpp
        stacsos/kernel/src/arch/x86/x2apic.cpp
        stacsos/kernel/src/arch/x86/x86-core.cpp
        stacsos/kernel/src/arch/x86/x86-page-table.cpp
        stacsos/kernel/src/arch/x86/x86-platform.cpp
        stacsos/kernel/src/arch/core-manager.cpp
        stacsos/kernel/src/arch/core.cpp
        stacsos/kernel/src/dev/acpi/acpi.cpp
        stacsos/kernel/src/dev/console/physical-console.cpp
        stacsos/kernel/src/dev/console/virtual-console.cpp
        stacsos/kernel/src/dev/gfx/graphics.cpp
        stacsos/kernel/src/dev/gfx/qemu-stdvga.cpp
        stacsos/kernel/src/dev/input/keyboard.cpp
        stacsos/kernel/src/dev/misc/cmos-rtc.cpp
        stacsos/kernel/src/dev/misc/rtc.cpp
        stacsos/kernel/src/dev/pci/pci-device.cpp
        stacsos/kernel/src/dev/pci/pci-express-bus.cpp
        stacsos/kernel/src/dev/storage/ahci-controller.cpp
        stacsos/kernel/src/dev/storage/ahci-storage-device.cpp
        stacsos/kernel/src/dev/storage/block-device.cpp
        stacsos/kernel/src/dev/tty/terminal.cpp
        stacsos/kernel/src/dev/devfs.cpp
        stacsos/kernel/src/dev/device-class.cpp
        stacsos/kernel/src/dev/device-manager.cpp
        stacsos/kernel/src/fs/filesystem.cpp
        stacsos/kernel/src/fs/fs-node.cpp
        stacsos/kernel/src/fs/tar-filesystem.cpp
        stacsos/kernel/src/fs/vfs.cpp
        stacsos/kernel/src/mem/address-space-region.cpp
        stacsos/kernel/src/mem/address-space.cpp
        stacsos/kernel/src/mem/large-object-allocator.cpp
        stacsos/kernel/src/mem/memory-manager.cpp
        stacsos/kernel/src/mem/new.cpp
        stacsos/kernel/src/mem/object-allocator.cpp
        stacsos/kernel/src/mem/page-allocator-buddy.cpp
        stacsos/kernel/src/mem/page-allocator-linear.cpp
        stacsos/kernel/src/mem/page-allocator.cpp
        stacsos/kernel/src/mem/page-table-allocator.cpp
        stacsos/kernel/src/mem/slab-cache.cpp
        stacsos/kernel/src/obj/object-manager.cpp
        stacsos/kernel/src/obj/object.cpp
        stacsos/kernel/src/sched/alg/priority.cpp
        stacsos/kernel/src/sched/alg/rr.cpp
        stacsos/kernel/src/sched/alg/sfs.cpp
        stacsos/kernel/src/sched/event.cpp
        stacsos/kernel/src/sched/process-manager.cpp
        stacsos/kernel/src/sched/process.cpp
        stacsos/kernel/src/sched/scheduler.cpp
        stacsos/kernel/src/sched/sleeper.cpp
        stacsos/kernel/src/sched/thread.cpp
        stacsos/kernel/src/support/guard.cpp
        stacsos/kernel/src/config.cpp
        stacsos/kernel/src/debug.cpp
        stacsos/kernel/src/lock.cpp
        stacsos/kernel/src/main.cpp
        stacsos/kernel/src/syscall.cpp
        stacsos/lib/inc/stacsos/atomic.h
        stacsos/lib/inc/stacsos/avl-tree.h
        stacsos/lib/inc/stacsos/bitset.h
        stacsos/lib/inc/stacsos/elf.h
        stacsos/lib/inc/stacsos/helpers.h
        stacsos/lib/inc/stacsos/list.h
        stacsos/lib/inc/stacsos/map.h
        stacsos/lib/inc/stacsos/memops.h
        stacsos/lib/inc/stacsos/memory.h
        stacsos/lib/inc/stacsos/optional.h
        stacsos/lib/inc/stacsos/printf.h
        stacsos/lib/inc/stacsos/string.h
        stacsos/lib/inc/stacsos/syscalls.h
        stacsos/lib/inc/stacsos/vector.h
        stacsos/lib/inc/global.h
        stacsos/lib/inc/stacsos-config.h
        stacsos/lib/src/printf.cpp
        stacsos/lib/src/string.cpp
        stacsos/user/cat/src/main.cpp
        stacsos/user/init/src/main.cpp
        stacsos/user/mandelbrot/src/main.cpp
        stacsos/user/poweroff/src/main.cpp
        stacsos/user/sched-test/src/main.cpp
        stacsos/user/sched-test2/src/main.cpp
        stacsos/user/shell/src/main.cpp
        stacsos/user/ulib/inc/stacsos/console.h
        stacsos/user/ulib/inc/stacsos/objects.h
        stacsos/user/ulib/inc/stacsos/process.h
        stacsos/user/ulib/inc/stacsos/threads.h
        stacsos/user/ulib/inc/stacsos/user-syscall.h
        stacsos/user/ulib/src/console.cpp
        stacsos/user/ulib/src/entry.cpp
        stacsos/user/ulib/src/guard.cpp
        stacsos/user/ulib/src/mem.cpp
        stacsos/user/ulib/src/objects.cpp
        stacsos/user/ulib/src/process.cpp
        stacsos/user/ulib/src/support.cpp
        stacsos/user/ulib/src/threads.cpp)
