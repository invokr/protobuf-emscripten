## Process this file with automake to produce Makefile.in

if HAVE_ZLIB
GZCHECKPROGRAMS = zcgzip zcgunzip
GZHEADERS = google/protobuf/io/gzip_stream.h
GZTESTS = google/protobuf/io/gzip_stream_unittest.sh
ZLIB_DEF = -DHAVE_ZLIB=1
else
GZCHECKPROGRAMS =
GZHEADERS =
GZTESTS =
ZLIB_DEF =
endif

if HAVE_PTHREAD
PTHREAD_DEF = -DHAVE_PTHREAD=1
else
PTHREAD_DEF =
endif

if GCC
# Turn on all warnings except for sign comparison (we ignore sign comparison
# in Google so our code base have tons of such warnings).
NO_OPT_CXXFLAGS = $(PTHREAD_CFLAGS) $(PTHREAD_DEF) $(ZLIB_DEF) -Wall -Wno-sign-compare
else
NO_OPT_CXXFLAGS = $(PTHREAD_CFLAGS) $(PTHREAD_DEF) $(ZLIB_DEF)
endif

AM_CXXFLAGS = $(NO_OPT_CXXFLAGS) $(PROTOBUF_OPT_FLAG)

AM_LDFLAGS = $(PTHREAD_CFLAGS)

# If I say "dist_include_DATA", automake complains that $(includedir) is not
# a "legitimate" directory for DATA.  Screw you, automake.
protodir = $(includedir)

# If you are adding new files here, also remember to change the build files for
# all other languages, //protoc-artifacts/build-zip.sh and run
# //update_file_list.sh for bazel.
nobase_dist_proto_DATA = google/protobuf/descriptor.proto     \
                         google/protobuf/any.proto            \
                         google/protobuf/api.proto            \
                         google/protobuf/duration.proto       \
                         google/protobuf/empty.proto          \
                         google/protobuf/field_mask.proto     \
                         google/protobuf/source_context.proto \
                         google/protobuf/struct.proto         \
                         google/protobuf/timestamp.proto      \
                         google/protobuf/type.proto           \
                         google/protobuf/wrappers.proto       \
                         google/protobuf/compiler/plugin.proto

# Not sure why these don't get cleaned automatically.
clean-local:
	rm -f *.loT

CLEANFILES = $(protoc_outputs) unittest_proto_middleman \
             testzip.jar testzip.list testzip.proto testzip.zip \
             no_warning_test.cc

MAINTAINERCLEANFILES =   \
  Makefile.in

nobase_include_HEADERS =                                        \
  google/protobuf/stubs/atomic_sequence_num.h                   \
  google/protobuf/stubs/atomicops.h                             \
  google/protobuf/stubs/atomicops_internals_emscripten.h        \
  google/protobuf/stubs/atomicops_internals_power.h             \
  google/protobuf/stubs/atomicops_internals_ppc_gcc.h           \
  google/protobuf/stubs/atomicops_internals_arm64_gcc.h         \
  google/protobuf/stubs/atomicops_internals_arm_gcc.h           \
  google/protobuf/stubs/atomicops_internals_arm_qnx.h           \
  google/protobuf/stubs/atomicops_internals_atomicword_compat.h \
  google/protobuf/stubs/atomicops_internals_generic_gcc.h       \
  google/protobuf/stubs/atomicops_internals_macosx.h            \
  google/protobuf/stubs/atomicops_internals_mips_gcc.h          \
  google/protobuf/stubs/atomicops_internals_pnacl.h             \
  google/protobuf/stubs/atomicops_internals_solaris.h           \
  google/protobuf/stubs/atomicops_internals_tsan.h              \
  google/protobuf/stubs/atomicops_internals_x86_gcc.h           \
  google/protobuf/stubs/atomicops_internals_x86_msvc.h          \
  google/protobuf/stubs/callback.h                              \
  google/protobuf/stubs/bytestream.h                            \
  google/protobuf/stubs/casts.h                                 \
  google/protobuf/stubs/common.h                                \
  google/protobuf/stubs/fastmem.h                               \
  google/protobuf/stubs/hash.h                                  \
  google/protobuf/stubs/logging.h                               \
  google/protobuf/stubs/macros.h                                \
  google/protobuf/stubs/mutex.h                                 \
  google/protobuf/stubs/once.h                                  \
  google/protobuf/stubs/platform_macros.h                       \
  google/protobuf/stubs/port.h                                  \
  google/protobuf/stubs/scoped_ptr.h                            \
  google/protobuf/stubs/shared_ptr.h                            \
  google/protobuf/stubs/singleton.h                             \
  google/protobuf/stubs/status.h                                \
  google/protobuf/stubs/stl_util.h                              \
  google/protobuf/stubs/stringpiece.h                           \
  google/protobuf/stubs/template_util.h                         \
  google/protobuf/stubs/type_traits.h                           \
  google/protobuf/any.pb.h                                      \
  google/protobuf/api.pb.h                                      \
  google/protobuf/any.h                                         \
  google/protobuf/arena.h                                       \
  google/protobuf/arenastring.h                                 \
  google/protobuf/descriptor_database.h                         \
  google/protobuf/descriptor.h                                  \
  google/protobuf/descriptor.pb.h                               \
  google/protobuf/duration.pb.h                                 \
  google/protobuf/dynamic_message.h                             \
  google/protobuf/empty.pb.h                                    \
  google/protobuf/extension_set.h                               \
  google/protobuf/field_mask.pb.h                               \
  google/protobuf/generated_enum_reflection.h                   \
  google/protobuf/generated_enum_util.h                         \
  google/protobuf/generated_message_reflection.h                \
  google/protobuf/generated_message_util.h                      \
  google/protobuf/has_bits.h                                    \
  google/protobuf/map_entry.h                                   \
  google/protobuf/map_entry_lite.h                              \
  google/protobuf/map_field.h                                   \
  google/protobuf/map_field_inl.h                               \
  google/protobuf/map_field_lite.h                              \
  google/protobuf/map.h                                         \
  google/protobuf/map_type_handler.h                            \
  google/protobuf/message.h                                     \
  google/protobuf/message_lite.h                                \
  google/protobuf/metadata.h                                    \
  google/protobuf/reflection.h                                  \
  google/protobuf/reflection_ops.h                              \
  google/protobuf/repeated_field.h                              \
  google/protobuf/service.h                                     \
  google/protobuf/source_context.pb.h                           \
  google/protobuf/struct.pb.h                                   \
  google/protobuf/text_format.h                                 \
  google/protobuf/timestamp.pb.h                                \
  google/protobuf/type.pb.h                                     \
  google/protobuf/unknown_field_set.h                           \
  google/protobuf/wire_format.h                                 \
  google/protobuf/wire_format_lite.h                            \
  google/protobuf/wire_format_lite_inl.h                        \
  google/protobuf/wrappers.pb.h                                 \
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
  google/protobuf/compiler/csharp/csharp_generator.h            \
  google/protobuf/compiler/csharp/csharp_names.h                \
  google/protobuf/compiler/java/java_generator.h                \
  google/protobuf/compiler/java/java_names.h                    \
  google/protobuf/compiler/javanano/javanano_generator.h        \
  google/protobuf/compiler/js/js_generator.h                    \
  google/protobuf/compiler/objectivec/objectivec_generator.h    \
  google/protobuf/compiler/objectivec/objectivec_helpers.h      \
  google/protobuf/compiler/php/php_generator.h                  \
  google/protobuf/compiler/python/python_generator.h            \
  google/protobuf/compiler/ruby/ruby_generator.h                \
  google/protobuf/util/type_resolver.h                          \
  google/protobuf/util/field_comparator.h                       \
  google/protobuf/util/field_mask_util.h                        \
  google/protobuf/util/json_util.h                              \
  google/protobuf/util/time_util.h                              \
  google/protobuf/util/type_resolver_util.h                     \
  google/protobuf/util/message_differencer.h

lib_LTLIBRARIES = libprotobuf-lite.la libprotobuf.la 

libprotobuf_lite_la_LIBADD = $(PTHREAD_LIBS)
libprotobuf_lite_la_LDFLAGS = -version-info 11:0:0 -export-dynamic -no-undefined
libprotobuf_lite_la_SOURCES =                                  \
  google/protobuf/stubs/atomicops_internals_x86_gcc.cc         \
  google/protobuf/stubs/atomicops_internals_x86_msvc.cc        \
  google/protobuf/stubs/bytestream.cc                          \
  google/protobuf/stubs/bytestream.h                           \
  google/protobuf/stubs/common.cc                              \
  google/protobuf/stubs/hash.h                                 \
  google/protobuf/stubs/int128.cc                              \
  google/protobuf/stubs/int128.h                               \
  google/protobuf/stubs/map_util.h                             \
  google/protobuf/stubs/mathutil.h                             \
  google/protobuf/stubs/once.cc                                \
  google/protobuf/stubs/shared_ptr.h                           \
  google/protobuf/stubs/status.cc                              \
  google/protobuf/stubs/status.h                               \
  google/protobuf/stubs/status_macros.h                        \
  google/protobuf/stubs/statusor.cc                            \
  google/protobuf/stubs/statusor.h                             \
  google/protobuf/stubs/stringpiece.cc                         \
  google/protobuf/stubs/stringpiece.h                          \
  google/protobuf/stubs/stringprintf.cc                        \
  google/protobuf/stubs/stringprintf.h                         \
  google/protobuf/stubs/structurally_valid.cc                  \
  google/protobuf/stubs/strutil.cc                             \
  google/protobuf/stubs/strutil.h                              \
  google/protobuf/stubs/time.cc                                \
  google/protobuf/stubs/time.h                                 \
  google/protobuf/arena.cc                                     \
  google/protobuf/arenastring.cc                               \
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
libprotobuf_la_LDFLAGS = -version-info 11:0:0 -export-dynamic -no-undefined
libprotobuf_la_SOURCES =                                       \
  $(libprotobuf_lite_la_SOURCES)                               \
  google/protobuf/any.pb.cc                                    \
  google/protobuf/api.pb.cc                                    \
  google/protobuf/stubs/mathlimits.cc                          \
  google/protobuf/stubs/mathlimits.h                           \
  google/protobuf/any.cc                                       \
  google/protobuf/descriptor.cc                                \
  google/protobuf/descriptor_database.cc                       \
  google/protobuf/descriptor.pb.cc                             \
  google/protobuf/duration.pb.cc                               \
  google/protobuf/dynamic_message.cc                           \
  google/protobuf/empty.pb.cc                                  \
  google/protobuf/extension_set_heavy.cc                       \
  google/protobuf/field_mask.pb.cc                             \
  google/protobuf/generated_message_reflection.cc              \
  google/protobuf/map_field.cc                                 \
  google/protobuf/message.cc                                   \
  google/protobuf/reflection_internal.h                        \
  google/protobuf/reflection_ops.cc                            \
  google/protobuf/service.cc                                   \
  google/protobuf/source_context.pb.cc                         \
  google/protobuf/struct.pb.cc                                 \
  google/protobuf/stubs/substitute.cc                          \
  google/protobuf/stubs/substitute.h                           \
  google/protobuf/text_format.cc                               \
  google/protobuf/timestamp.pb.cc                              \
  google/protobuf/type.pb.cc                                   \
  google/protobuf/unknown_field_set.cc                         \
  google/protobuf/wire_format.cc                               \
  google/protobuf/wrappers.pb.cc                               \
  google/protobuf/io/gzip_stream.cc                            \
  google/protobuf/io/printer.cc                                \
  google/protobuf/io/strtod.cc                                 \
  google/protobuf/io/tokenizer.cc                              \
  google/protobuf/io/zero_copy_stream_impl.cc                  \
  google/protobuf/compiler/importer.cc                         \
  google/protobuf/compiler/parser.cc                           \
  google/protobuf/util/field_comparator.cc                     \
  google/protobuf/util/field_mask_util.cc                      \
  google/protobuf/util/internal/constants.h                    \
  google/protobuf/util/internal/datapiece.cc                   \
  google/protobuf/util/internal/datapiece.h                    \
  google/protobuf/util/internal/default_value_objectwriter.cc  \
  google/protobuf/util/internal/default_value_objectwriter.h   \
  google/protobuf/util/internal/error_listener.cc              \
  google/protobuf/util/internal/error_listener.h               \
  google/protobuf/util/internal/expecting_objectwriter.h       \
  google/protobuf/util/internal/field_mask_utility.cc          \
  google/protobuf/util/internal/field_mask_utility.h           \
  google/protobuf/util/internal/json_escaping.cc               \
  google/protobuf/util/internal/json_escaping.h                \
  google/protobuf/util/internal/json_objectwriter.cc           \
  google/protobuf/util/internal/json_objectwriter.h            \
  google/protobuf/util/internal/json_stream_parser.cc          \
  google/protobuf/util/internal/json_stream_parser.h           \
  google/protobuf/util/internal/location_tracker.h             \
  google/protobuf/util/internal/mock_error_listener.h          \
  google/protobuf/util/internal/object_location_tracker.h      \
  google/protobuf/util/internal/object_source.h                \
  google/protobuf/util/internal/object_writer.cc               \
  google/protobuf/util/internal/object_writer.h                \
  google/protobuf/util/internal/protostream_objectsource.cc    \
  google/protobuf/util/internal/protostream_objectsource.h     \
  google/protobuf/util/internal/protostream_objectwriter.cc    \
  google/protobuf/util/internal/protostream_objectwriter.h     \
  google/protobuf/util/internal/proto_writer.cc                \
  google/protobuf/util/internal/proto_writer.h                 \
  google/protobuf/util/internal/structured_objectwriter.h      \
  google/protobuf/util/internal/type_info.cc                   \
  google/protobuf/util/internal/type_info.h                    \
  google/protobuf/util/internal/type_info_test_helper.cc       \
  google/protobuf/util/internal/type_info_test_helper.h        \
  google/protobuf/util/internal/utility.cc                     \
  google/protobuf/util/internal/utility.h                      \
  google/protobuf/util/json_util.cc                            \
  google/protobuf/util/message_differencer.cc                  \
  google/protobuf/util/time_util.cc                            \
  google/protobuf/util/type_resolver_util.cc

nodist_libprotobuf_la_SOURCES = $(nodist_libprotobuf_lite_la_SOURCES)
