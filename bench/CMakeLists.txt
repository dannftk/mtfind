find_package(Threads REQUIRED)

set(SOURCES
    main.cpp
)

set(HEADERS
    ${MTFIND_SRC_DIR}/aux/chunk.hpp
    ${MTFIND_SRC_DIR}/aux/chunk_handler.hpp
    ${MTFIND_SRC_DIR}/aux/iterator_concept.hpp
    ${MTFIND_SRC_DIR}/splitters/stream_splitter.hpp
    ${MTFIND_SRC_DIR}/processors/multithreaded_task_processor.hpp
    ${MTFIND_SRC_DIR}/processors/threaded_chunk_processor.hpp
    ${MTFIND_SRC_DIR}/searchers/boyer_moore_searcher.hpp
    ${MTFIND_SRC_DIR}/searchers/naive_searcher.hpp
    ${MTFIND_SRC_DIR}/splitters/range_splitter.hpp
    ${MTFIND_SRC_DIR}/strat/divide_and_conquer.hpp
    ${MTFIND_SRC_DIR}/strat/round_robin.hpp
    ${MTFIND_SRC_DIR}/tokenizers/range_tokenizer.hpp
)

add_executable(mtfind_bench ${SOURCES} ${HEADERS})
target_include_directories(mtfind_bench PRIVATE ${CMAKE_CURRENT_LIST_DIR} ${MTFIND_SRC_DIR})

target_link_libraries(mtfind_bench PRIVATE Threads::Threads)
target_link_libraries(mtfind_bench PRIVATE CONAN_PKG::boost)
target_link_libraries(mtfind_bench PRIVATE CONAN_PKG::benchmark)
