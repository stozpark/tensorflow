# Description:
# TensorFlow SavedModel.

package(
    default_visibility = ["//visibility:public"],
)

licenses(["notice"])  # Apache 2.0

exports_files(["LICENSE"])

load("//tensorflow:tensorflow.bzl", "tf_cc_test")

cc_library(
    name = "constants",
    hdrs = ["constants.h"],
)

cc_library(
    name = "signature_constants",
    hdrs = ["signature_constants.h"],
)

cc_library(
    name = "tag_constants",
    hdrs = ["tag_constants.h"],
)

cc_library(
    name = "loader",
    srcs = ["loader.cc"],
    hdrs = ["loader.h"],
    deps = [
        ":constants",
        "//tensorflow/core:core_cpu",
        "//tensorflow/core:lib",
        "//tensorflow/core:lib_internal",
        "//tensorflow/core:protos_all_cc",
        "//tensorflow/core:tensorflow",
        "//tensorflow/core/util/tensor_bundle:naming",
    ],
)

# Reenable target once half_plus_two_data does not run TF during build.
# tf_cc_test(
#     name = "loader_test",
#     srcs = ["loader_test.cc"],
#     data = [
#         "//tensorflow/python/saved_model/example:saved_model_half_plus_two_data",
#     ],
#     linkstatic = 1,
#     tags = ["manual"],
#     deps = [
#         ":constants",
#         ":loader",
#         ":signature_constants",
#         ":tag_constants",
#         "//tensorflow/core:lib",
#         "//tensorflow/core:protos_all_cc",
#         "//tensorflow/core:test",
#         "//tensorflow/core:test_main",
#         "//tensorflow/core:testlib",
#     ],
# )

# -----------------------------------------------------------------------------
# Google-internal targets.

filegroup(
    name = "all_files",
    srcs = glob(
        ["**/*"],
        exclude = [
            "**/METADATA",
            "**/OWNERS",
        ],
    ),
    visibility = ["//tensorflow:__subpackages__"],
)
