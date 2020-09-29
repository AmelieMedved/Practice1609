cmake_minimum_required(VERSION 3.18.3) #Проверка версии CMake.

set (PROJECT_NAME Test) #Создаем обычную локальную переменную с именем проекта (PROJECT_NAME - имя, Test - Значение)

set(CMAKE_CONFIGURATION_TYPES "Debug;Release" CACHE STRING "Configs" FORCE) 
#Создается переменная CMAKE_CONFIGURATION_TYPES со значением "Debug;Release" и меткой/разделом Configs,
#переменная сохраняется в специальном файле доступном из всех файлов.
if (NOT CMAKE_BUILD_TYPE) #Проверка имеющихся у компилятора вариантов сборки
	set(CMAKE_BUILD_TYPE Release) #Если нет, то устаналиваем Release
endif()

file (GLOB hdrs "*.h") #Добавляем в переменную hdrs все файлы с расширением .h
file (GLOB srcs "*.cpp") #Добавляем в переменную srcs все файлы с расширением .cpp

add_executable(${PROJECT_NAME} ${srcs} ${hdrs}) #Создаем проект с именем из переменной ${PROJECT_NAME}, в него добавляются файлы из переменных ${srcs} и ${hdrs}