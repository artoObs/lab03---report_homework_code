# lab03---report_homework_code

# Коды из файлов homework лабораторной №3

## Директория formatter_lib

  **CMakeLists.txt**

   ```bash
   cmake_minimum_required(VERSION 3.4)
   project(formatter)
   set(CMAKE_CXX_STANDARD 11)
   set(CMAKE_CXX_STANDARD_REQUIRED ON)
   add_library(formatter STATIC ${CMAKE_CURRENT_SOURCE_DIR}/formatter.cpp)
   include_directories(${CMAKE_CURRENT_SOURCE_DIR})
   ```

  **formatter.cpp**

    ```bash                      
    #include "formatter.h"
  
    std::string formatter(const std::string& message)
    {
        std::string res;
        res += "-------------------------\n";
        res += message + "\n";
        res += "-------------------------\n";
        return res;
    }
    ```

  **formatter.h**

    ```bash
    #pragma once
    
    #include <string>
    
    std::string formatter(const std::string& message);
    ```

## Директория formatter_ex_lib

  **CMakeLists.txt**

    ```bash
    cmake_minimum_required(VERSION 3.4)
    project(formatter_ex)
    
    set(CMAKE_CXX_STANDARD 11)
    set(CMAKE_CXX_STANDARD_REQUIRED ON)
    
    add_subdirectory(../formatter_lib formatter_lib)
    
    add_library(formatter_ex STATIC formatter_ex.cpp)
    
    include_directories(${CMAKE_CURRENT_SOURCE_DIR})
    
    target_link_libraries(formatter_ex PRIVATE formatter)
    ```

## Директория hello_world

  **CMakeLists.txt**

    ```bash
    cmake_minimum_required(VERSION 3.4)
    project(hello_world)
    
    set(CMAKE_CXX_STANDARD 11)
    set(CMAKE_CXX_STANDARD_REQUIRED ON)
    
    add_subdirectory(../formatter_ex_lib formatter_ex_lib)
    
    add_executable(hello_world main.cpp)
    
    target_link_libraries(hello_world PRIVATE formatter_ex)
    ```

  **main.cpp**
  
  > Файл-затычка, код предположительный
  
    ```bash                              
    #include <iostream>
    #include "formatter_ex.h"
    
    int main() {
        std::cout << formatter("Hello, World!") << std::endl;
        return 0;
    }
    ```

## Директория solver

  **CMakeLists.txt**

    ```bash
    cmake_minimum_required(VERSION 3.4)
    project(hello_world)
    
    set(CMAKE_CXX_STANDARD 11)
    set(CMAKE_CXX_STANDARD_REQUIRED ON)
    
    add_subdirectory(../formatter_ex_lib formatter_ex_lib)
    add_subdirectory(../solver_lib solver_lib)
    
    add_executable(solver main.cpp)
    
    target_link_libraries(solver PRIVATE formatter_ex solver_lib)
    ```

  **main.cpp**

  > Файл-затычка, кода нет

## Директория solver_lib

  **CMakeLists.txt**

    ```bash
    cmake_minimum_required(VERSION 3.4)
    project(solver_lib)
    
    add_library(solver_lib STATIC solver.cpp)
    include_directories(${CMAKE_CURRENT_SOURCE_DIR})
    ```

  **solver.cpp**

  > Заглушка

  **solver.h**

  > Заглушка
