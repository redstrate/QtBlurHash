# SPDX-FileCopyrightText: Joshua Goins <josh@redstrate.com>
# SPDX-License-Identifier: BSD-2-Clause

ecm_add_test(testblurhash.cpp
        TEST_NAME testblurhash
        LINK_LIBRARIES blurhash_qt Qt::Test
)