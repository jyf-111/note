## # WIN32_EXECUTABLE TRUE 解决控制台输出问题  
## database query 作用域必须database.open() 正解: query构造query(database)指定database
##
'''
if(MSVC)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /std:c++17 /Zc:__cplusplus")
endif(MSVC)
'''

error: Must use 'class' tag to refer to type 'yolo' in this scope (fix available)
有重名 :::: 解决办法 new class classname

set(CMAKE_PREFIX_PATH C:/Users/jyf/tool/Qt/6.2.4/msvc2019_64/lib/cmake/Qt6)