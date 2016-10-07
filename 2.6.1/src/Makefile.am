## Process this file with automake to produce Makefile.in

if HAVE_ZLIB
GZCHECKPROGRAMS = zcgzip zcgunzip
GZHEADERS = google/protobuf/io/gzip_stream.h
GZTESTS = google/protobuf/io/gzip_stream_unittest.sh
else
GZCHECKPROGRAMS =
GZHEADERS =
GZTESTS =
endif

if GCC
# These are good warnings to turn on by default
NO_OPT_CXXFLAGS = $(PTHREAD_CFLAGS) -Wall -Wwrite-strings -Woverloaded-virtual -Wno-sign-compare
else
NO_OPT_CXXFLAGS = $(PTHREAD_CFLAGS)
endif

AM_CXXFLAGS = $(NO_OPT_CXXFLAGS) $(PROTOBUF_OPT_FLAG) -Wno-unused-local-typedef

AM_LDFLAGS = $(PTHREAD_CFLAGS)

# If I say "dist_include_DATA", automake complains that $(includedir) is not
# a "legitimate" directory for DATA.  Screw you, automake.
protodir = $(includedir)
nobase_dist_proto_DATA = google/protobuf/descriptor.proto \
                         google/protobuf/compiler/plugin.proto

# Not sure why these don't get cleaned automatically.
clean-local:
	rm -f *.loT

CLEANFILES = $(protoc_outputs) unittest_proto_middleman \
             testzip.jar testzip.list testzip.proto testzip.zip

MAINTAINERCLEANFILES =   \
  Makefile.in

nobase_include_HEADERS =                                        \
  google/protobuf/stubs/atomicops.h                             \
  google/protobuf/stubs/atomicops_internals_arm_gcc.h           \
  google/protobuf/stubs/atomicops_internals_arm64_gcc.h         \
  google/protobuf/stubs/atomicops_internals_arm_qnx.h           \
  google/protobuf/stubs/atomicops_internals_atomicword_compat.h \
  google/protobuf/stubs/atomicops_internals_generic_gcc.h       \
  google/protobuf/stubs/atomicops_internals_macosx.h            \
  google/protobuf/stubs/atomicops_internals_mips_gcc.h          \
  google/protobuf/stubs/atomicops_internals_pnacl.h             \
  google/protobuf/stubs/atomicops_internals_tsan.h              \
  google/protobuf/stubs/atomicops_internals_x86_gcc.h           \
  google/protobuf/stubs/atomicops_internals_x86_msvc.h          \
  google/protobuf/stubs/common.h                                \
  google/protobuf/stubs/platform_macros.h                       \
  google/protobuf/stubs/once.h                                  \
  google/protobuf/stubs/stl_util.h                              \
  google/protobuf/stubs/template_util.h                         \
  google/protobuf/stubs/type_traits.h                           \
  google/protobuf/descriptor.h                                  \
  google/protobuf/descriptor.pb.h                               \
  google/protobuf/descriptor_database.h                         \
  google/protobuf/dynamic_message.h                             \
  google/protobuf/extension_set.h                               \
  google/protobuf/generated_enum_reflection.h                   \
  google/protobuf/generated_message_util.h                      \
  google/protobuf/generated_message_reflection.h                \
  google/protobuf/message.h                                     \
  google/protobuf/message_lite.h                                \
  google/protobuf/reflection_ops.h                              \
  google/protobuf/repeated_field.h                              \
  google/protobuf/service.h                                     \
  google/protobuf/text_format.h                                 \
  google/protobuf/unknown_field_set.h                           \
  google/protobuf/wire_format.h                                 \
  google/protobuf/wire_format_lite.h                            \
  google/protobuf/wire_format_lite_inl.h                        \
  google/protobuf/io/coded_stream.h                             \
  $(GZHEADERS)                                                  \
  google/protobuf/io/printer.h                                  \
  google/protobuf/io/strtod.h                                   \
  google/protobuf/io/tokenizer.h                                \
  google/protobuf/io/zero_copy_stream.h                         \
  google/protobuf/io/zero_copy_stream_impl.h                    \
  google/protobuf/io/zero_copy_stream_impl_lite.h               \
  google/protobuf/compiler/code_generator.h                     \
  google/protobuf/compiler/command_line_interface.h             \
  google/protobuf/compiler/importer.h                           \
  google/protobuf/compiler/parser.h                             \
  google/protobuf/compiler/plugin.h                             \
  google/protobuf/compiler/plugin.pb.h                          \
  google/protobuf/compiler/cpp/cpp_generator.h                  \
  google/protobuf/compiler/java/java_generator.h                \
  google/protobuf/compiler/python/python_generator.h

lib_LTLIBRARIES = libprotobuf-lite.la libprotobuf.la libprotoc.la

libprotobuf_lite_la_LIBADD = $(PTHREAD_LIBS)
libprotobuf_lite_la_LDFLAGS = -version-info 9:1:0 -export-dynamic -no-undefined
libprotobuf_lite_la_SOURCES =                                  \
  google/protobuf/stubs/atomicops_internals_x86_gcc.cc         \
  google/protobuf/stubs/atomicops_internals_x86_msvc.cc        \
  google/protobuf/stubs/common.cc                              \
  google/protobuf/stubs/once.cc                                \
  google/protobuf/stubs/hash.h                                 \
  google/protobuf/stubs/map_util.h                             \
  google/protobuf/stubs/shared_ptr.h                           \
  google/protobuf/stubs/stringprintf.cc                        \
  google/protobuf/stubs/stringprintf.h                         \
  google/protobuf/extension_set.cc                             \
  google/protobuf/generated_message_util.cc                    \
  google/protobuf/message_lite.cc                              \
  google/protobuf/repeated_field.cc                            \
  google/protobuf/wire_format_lite.cc                          \
  google/protobuf/io/coded_stream.cc                           \
  google/protobuf/io/coded_stream_inl.h                        \
  google/protobuf/io/zero_copy_stream.cc                       \
  google/protobuf/io/zero_copy_stream_impl_lite.cc

libprotobuf_la_LIBADD = $(PTHREAD_LIBS)
libprotobuf_la_LDFLAGS = -version-info 9:1:0 -export-dynamic -no-undefined
libprotobuf_la_SOURCES =                                       \
  $(libprotobuf_lite_la_SOURCES)                               \
  google/protobuf/stubs/strutil.cc                             \
  google/protobuf/stubs/strutil.h                              \
  google/protobuf/stubs/substitute.cc                          \
  google/protobuf/stubs/substitute.h                           \
  google/protobuf/stubs/structurally_valid.cc                  \
  google/protobuf/descriptor.cc                                \
  google/protobuf/descriptor.pb.cc                             \
  google/protobuf/descriptor_database.cc                       \
  google/protobuf/dynamic_message.cc                           \
  google/protobuf/extension_set_heavy.cc                       \
  google/protobuf/generated_message_reflection.cc              \
  google/protobuf/message.cc                                   \
  google/protobuf/reflection_ops.cc                            \
  google/protobuf/service.cc                                   \
  google/protobuf/text_format.cc                               \
  google/protobuf/unknown_field_set.cc                         \
  google/protobuf/wire_format.cc                               \
  google/protobuf/io/gzip_stream.cc                            \
  google/protobuf/io/printer.cc                                \
  google/protobuf/io/strtod.cc                                 \
  google/protobuf/io/tokenizer.cc                              \
  google/protobuf/io/zero_copy_stream_impl.cc                  \
  google/protobuf/compiler/importer.cc                         \
  google/protobuf/compiler/parser.cc

libprotoc_la_LIBADD = $(PTHREAD_LIBS) libprotobuf.la
libprotoc_la_LDFLAGS = -version-info 9:1:0 -export-dynamic -no-undefined
libprotoc_la_SOURCES =                                         \
  google/protobuf/compiler/code_generator.cc                   \
  google/protobuf/compiler/command_line_interface.cc           \
  google/protobuf/compiler/plugin.cc                           \
  google/protobuf/compiler/plugin.pb.cc                        \
  google/protobuf/compiler/subprocess.cc                       \
  google/protobuf/compiler/subprocess.h                        \
  google/protobuf/compiler/zip_writer.cc                       \
  google/protobuf/compiler/zip_writer.h                        \
  google/protobuf/compiler/cpp/cpp_enum.cc                     \
  google/protobuf/compiler/cpp/cpp_enum.h                      \
  google/protobuf/compiler/cpp/cpp_enum_field.cc               \
  google/protobuf/compiler/cpp/cpp_enum_field.h                \
  google/protobuf/compiler/cpp/cpp_extension.cc                \
  google/protobuf/compiler/cpp/cpp_extension.h                 \
  google/protobuf/compiler/cpp/cpp_field.cc                    \
  google/protobuf/compiler/cpp/cpp_field.h                     \
  google/protobuf/compiler/cpp/cpp_file.cc                     \
  google/protobuf/compiler/cpp/cpp_file.h                      \
  google/protobuf/compiler/cpp/cpp_generator.cc                \
  google/protobuf/compiler/cpp/cpp_helpers.cc                  \
  google/protobuf/compiler/cpp/cpp_helpers.h                   \
  google/protobuf/compiler/cpp/cpp_message.cc                  \
  google/protobuf/compiler/cpp/cpp_message.h                   \
  google/protobuf/compiler/cpp/cpp_message_field.cc            \
  google/protobuf/compiler/cpp/cpp_message_field.h             \
  google/protobuf/compiler/cpp/cpp_options.h                   \
  google/protobuf/compiler/cpp/cpp_primitive_field.cc          \
  google/protobuf/compiler/cpp/cpp_primitive_field.h           \
  google/protobuf/compiler/cpp/cpp_service.cc                  \
  google/protobuf/compiler/cpp/cpp_service.h                   \
  google/protobuf/compiler/cpp/cpp_string_field.cc             \
  google/protobuf/compiler/cpp/cpp_string_field.h              \
  google/protobuf/compiler/java/java_context.cc                \
  google/protobuf/compiler/java/java_context.h                 \
  google/protobuf/compiler/java/java_enum.cc                   \
  google/protobuf/compiler/java/java_enum.h                    \
  google/protobuf/compiler/java/java_enum_field.cc             \
  google/protobuf/compiler/java/java_enum_field.h              \
  google/protobuf/compiler/java/java_extension.cc              \
  google/protobuf/compiler/java/java_extension.h               \
  google/protobuf/compiler/java/java_field.cc                  \
  google/protobuf/compiler/java/java_field.h                   \
  google/protobuf/compiler/java/java_file.cc                   \
  google/protobuf/compiler/java/java_file.h                    \
  google/protobuf/compiler/java/java_generator.cc              \
  google/protobuf/compiler/java/java_generator_factory.cc      \
  google/protobuf/compiler/java/java_generator_factory.h       \
  google/protobuf/compiler/java/java_helpers.cc                \
  google/protobuf/compiler/java/java_helpers.h                 \
  google/protobuf/compiler/java/java_lazy_message_field.cc     \
  google/protobuf/compiler/java/java_lazy_message_field.h      \
  google/protobuf/compiler/java/java_message.cc                \
  google/protobuf/compiler/java/java_message.h                 \
  google/protobuf/compiler/java/java_message_field.cc          \
  google/protobuf/compiler/java/java_message_field.h           \
  google/protobuf/compiler/java/java_name_resolver.cc          \
  google/protobuf/compiler/java/java_name_resolver.h           \
  google/protobuf/compiler/java/java_primitive_field.cc        \
  google/protobuf/compiler/java/java_primitive_field.h         \
  google/protobuf/compiler/java/java_shared_code_generator.cc  \
  google/protobuf/compiler/java/java_shared_code_generator.h   \
  google/protobuf/compiler/java/java_service.cc                \
  google/protobuf/compiler/java/java_service.h                 \
  google/protobuf/compiler/java/java_string_field.cc           \
  google/protobuf/compiler/java/java_string_field.h            \
  google/protobuf/compiler/java/java_doc_comment.cc            \
  google/protobuf/compiler/java/java_doc_comment.h             \
  google/protobuf/compiler/python/python_generator.cc
