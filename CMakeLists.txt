cmake_minimum_required(VERSION 3.16)

# 프로젝트 설정
project(master_c
    VERSION 1.0
    LANGUAGES C
)

# C 표준 설정
set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_C_EXTENSIONS OFF)

# 소스 파일 목록을 직접 관리 (추천 방식)
# 새로운 .c 파일을 만들면 아래 리스트에 추가하고 저장하세요.
set(SOURCES
    "src/hello_world.c"
    "src/util.c"
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
    target_compile_options(${PROJECT_NAME} PRIVATE /W4)
else()
    target_compile_options(${PROJECT_NAME} PRIVATE -Wall -Wextra -Wpedantic)
endif()