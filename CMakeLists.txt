cmake_minimum_required(VERSION 3.22)
project(icp VERSION 1.0.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# --- Fetch FTXUI --------------------------------------------------------------
include(FetchContent)
FetchContent_Declare(ftxui
  GIT_REPOSITORY https://github.com/ArthurSonzogni/FTXUI
  GIT_TAG v7.0.3  # 替换为版本、标签或提交哈希
)
FetchContent_MakeAvailable(ftxui)
# ------------------------------------------------------------------------------

add_executable(icp main.cpp)

target_compile_features(icp PRIVATE cxx_std_20)

target_link_libraries(
  icp
  PRIVATE ftxui::screen
  PRIVATE ftxui::dom
  PRIVATE ftxui::component
)
