# Проверка минимальной версии cmake
cmake_minimum_required(VERSION 3.5)

# Название проекта
project(template)

# Переменная с именем исполняемого файла
set(EXECUTABLE ${PROJECT_NAME})

# Добавление файлов исходного кода
add_executable(
    ${EXECUTABLE} 
#    *.cpp
)

# Директории с *.h файлами
include_directories(
#    "include"
)

# Директории с wxWidgets и библиотеками
set(wxWidgets_ROOT_DIR "C:/Program Files (x86)/wxWidgets")
set(wxWidgets_LIB_DIR "C:/Program Files (x86)/wxWidgets/lib/gcc_x64_lib")

# Поск необходимых компонентов библиотек
find_package(wxWidgets COMPONENTS REQUIRED core base net)
include(${wxWidgets_USE_FILE})

# Подключение библиотек при компиляции
target_link_libraries(
    ${EXECUTABLE}
#   debug
    ${wxWidgets_LIBRARIES}  
)

# флаг компиляции для запуска приложения без командной строки
target_link_options(
    ${EXECUTABLE}
    PRIVATE
    -mwindows
)