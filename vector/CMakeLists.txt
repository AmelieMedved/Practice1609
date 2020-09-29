file (GLOB hdrs "*.h") #Добавляем в переменную hdrs все файлы с расширением .h
file (GLOB srcs "*.cpp") #Добавляем в переменную crcs все файлы с расширением .cpp
add_executable(${vector} ${srcs} ${hdrs}) #Создаем проект с именем из переменной ${vector}, в него добавляются все файлы из переменных ${srcs}
# и ${hdrs}
target_link_libraries(${vector} ${vectorlib}) #Подключаем к преокту с именем ${vector} библиотеку с именем ${vectorlib}

