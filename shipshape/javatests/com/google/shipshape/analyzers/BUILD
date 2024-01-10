java_test(
    name = "tests",
    srcs = glob(["*Test.java"]),
    data = [
        ":testdata",
        "//third_party/checkstyle",
    ],
    deps = [
        "//shipshape/java/com/google/shipshape/analyzers",
        "//shipshape/proto:note_proto_java",
        "//shipshape/proto:shipshape_context_proto_java",
        "//shipshape/proto:source_context_proto_java",
        "//shipshape/proto:textrange_proto_java",
        "//third_party/guava",
        "//third_party/hamcrest_all",
        "//third_party/junit",
    ],
)

filegroup(
    name = "testdata",
    srcs = glob(["testdata/**/*.*"]),
)
