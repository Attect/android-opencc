cmake_minimum_required(VERSION 3.4.1)
include_directories(src/main/cpp/opencc/deps/darts-clone)
include_directories(src/main/cpp/opencc/deps/rapidjson-0.11)
include_directories(src/main/cpp/opencc/deps/tclap-1.2.1)
include_directories(src/main/cpp/opencc)

set(
        LIBOPENCC_HEADERS
        src/main/cpp/opencc/BinaryDict.hpp
        src/main/cpp/opencc/Common.hpp
        src/main/cpp/opencc/Config.hpp
        src/main/cpp/opencc/Conversion.hpp
        src/main/cpp/opencc/ConversionChain.hpp
        src/main/cpp/opencc/Converter.hpp
        src/main/cpp/opencc/DartsDict.hpp
        src/main/cpp/opencc/Dict.hpp
        src/main/cpp/opencc/DictEntry.hpp
        src/main/cpp/opencc/DictGroup.hpp
        src/main/cpp/opencc/Exception.hpp
        src/main/cpp/opencc/Export.hpp
        src/main/cpp/opencc/Lexicon.hpp
        src/main/cpp/opencc/MaxMatchSegmentation.hpp
        src/main/cpp/opencc/Optional.hpp
        src/main/cpp/opencc/PhraseExtract.hpp
        src/main/cpp/opencc/Segmentation.hpp
        src/main/cpp/opencc/Segments.hpp
        src/main/cpp/opencc/SerializableDict.hpp
        src/main/cpp/opencc/SimpleConverter.hpp
        src/main/cpp/opencc/TextDict.hpp
        src/main/cpp/opencc/UTF8StringSlice.hpp
        src/main/cpp/opencc/UTF8Util.hpp
        src/main/cpp/opencc/opencc.h
)

set(
        LIBOPENCC_SOURCES
        src/main/cpp/opencc/BinaryDict.cpp
        src/main/cpp/opencc/Config.cpp
        src/main/cpp/opencc/Conversion.cpp
        src/main/cpp/opencc/ConversionChain.cpp
        src/main/cpp/opencc/Converter.cpp
        src/main/cpp/opencc/DartsDict.cpp
        src/main/cpp/opencc/Dict.cpp
        src/main/cpp/opencc/DictEntry.cpp
        src/main/cpp/opencc/DictGroup.cpp
        src/main/cpp/opencc/MaxMatchSegmentation.cpp
        src/main/cpp/opencc/PhraseExtract.cpp
        src/main/cpp/opencc/SimpleConverter.cpp
        src/main/cpp/opencc/Segmentation.cpp
        src/main/cpp/opencc/TextDict.cpp
        src/main/cpp/opencc/UTF8StringSlice.cpp
        src/main/cpp/opencc/UTF8Util.cpp
)


add_library(libopencc ${LIBOPENCC_SOURCES})

set_target_properties(
        libopencc
        PROPERTIES
        LINKER_LANGUAGE
        CXX
        OUTPUT_NAME
        opencc
        VERSION
        1.0.0
        SOVERSION
        2
)
link_libraries(libopencc)
add_library(lib-opencc-android SHARED src/main/cpp/chineseconverter.cpp)

install(
        TARGETS libopencc
        LIBRARY DESTINATION lib
        ARCHIVE DESTINATION lib
)

install(
        FILES ${LIBOPENCC_HEADERS}
        DESTINATION ${DIR_INCLUDE}/opencc
)
#
#add_library(
#    lib-opencc-android
#    SHARED
#    src/main/cpp/chineseconverter.cpp
#    )
#find_library(
#    log-lib
#    log
#    android
#    atomic
#    )