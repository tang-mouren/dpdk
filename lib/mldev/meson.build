# SPDX-License-Identifier: BSD-3-Clause
# Copyright (c) 2022 Marvell.

if is_windows
    build = false
    reason = 'not supported on Windows'
    subdir_done()
endif

sources = files(
        'rte_mldev_pmd.c',
        'rte_mldev.c',
        'mldev_utils.c',
        'mldev_utils_scalar.c',
)

if dpdk_conf.has('RTE_ARCH_ARM64')
    sources += files('mldev_utils_neon.c')
endif

headers = files(
        'rte_mldev.h',
)

indirect_headers += files(
        'rte_mldev_core.h',
)

driver_sdk_headers += files(
        'rte_mldev_pmd.h',
        'mldev_utils.h',
)

deps += ['mempool']

if get_option('buildtype').contains('debug')
        cflags += [ '-DRTE_LIBRTE_ML_DEV_DEBUG' ]
else
        cflags += [ '-URTE_LIBRTE_ML_DEV_DEBUG' ]
endif