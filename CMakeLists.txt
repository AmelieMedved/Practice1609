cmake_minimum_required(VERSION 3.18.3) #Проверка версии CMake.

set (PROJECT_NAME Vector_Test) # Создаем обычную локальную переменную с именем проекта (PROJECT_NAME - имя, Test - Значение)
project(${PROJECT_NAME}) # Название проекта

set(vector MyVector) #Переменная с именем приложения
set(vectorlib MyVectorLib) #Переменная с именем библиотека 

set(CMAKE_CONFIGURATION_TYPES "Debug;Release" CACHE STRING "Configs" FORCE) 
#Создается переменная CMAKE_CONFIGURATION_TYPES со значением "Debug;Release" и меткой/разделом Configs,
#переменная сохраняется в специальном файле доступном из всех файлов.
if (NOT CMAKE_BUILD_TYPE) #Проверка имеющихся у компилятора вариантов сборки
	set(CMAKE_BUILD_TYPE Release) #Если нет, то устаналиваем Release
endif()

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/vectorlib) #Добавляем директорию "${CMAKE_CURRENT_SOURCE_DIR}/vectorlib" в дополняемые
#каталоги включаемых файлов
#${CMAKE_CURRENT_SOURCE_DIR} - стандартная переменная с адресом рабочей директории CMakeList-а
#Подключение директории с h-файлами (Директория будет доступна для всех проектов)

add_subdirectory(vector) #Добавляем директорию с под-CMakeList-ом, и выполняем под-CmakeList
add_subdirectory(vectorlib) #Аналогично для директории vectorlib

# file (GLOB hdrs "*.h") #Добавляем в переменную hdrs все файлы с расширением .h
# file (GLOB srcs "*.cpp") #Добавляем в переменную srcs все файлы с расширением .cpp

# add_executable(${PROJECT_NAME} ${srcs} ${hdrs}) #Создаем проект с именем из переменной ${PROJECT_NAME}, в него добавляются файлы из переменных ${srcs} и ${hdrs}