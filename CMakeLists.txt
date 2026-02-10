cmake_minimum_required(VERSION 3.16)

# 프로젝트 언어를 C로 설정
project(master_c
    VERSION 1.0
    LANGUAGES C
)

# C 표준 설정 (C11 또는 C17 추천)
set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_C_EXTENSIONS OFF)

# src 디렉토리의 모든 .c 파일 수집
file(GLOB_RECURSE SOURCES
    "${CMAKE_SOURCE_DIR}/src/*.c"
)

# 실행 파일 생성
add_executable(${PROJECT_NAME} ${SOURCES})

# 헤더 파일 경로 설정
target_include_directories(${PROJECT_NAME}
    PRIVATE
    "${CMAKE_SOURCE_DIR}/src"
    "${CMAKE_SOURCE_DIR}/include"
)

# 컴파일러 경고 옵션 설정
if (MSVC)
    target_compile_options(${PROJECT_NAME}
        PRIVATE /W4
    )
else()
    target_compile_options(${PROJECT_NAME}
        PRIVATE -Wall -Wextra -Wpedantic
    )
endif()