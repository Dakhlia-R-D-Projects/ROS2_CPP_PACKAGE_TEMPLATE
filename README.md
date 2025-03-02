# Introduction
The porpose of this project is to facilitate the structured **ros2 c++ project** based on distributed libraries
# How To Use
1. Copy the libraries directiory inside your created package
2. Make the directory for your library  in the libraries directory (with ⚠ no spaces only under scores for spaces)
3. Inside the created directory create the .cpp and .hpp files
4. Just copy the CMakeLists.txt from the library_template to your create directory inside the libraries directory with no change in it
5. Copy the content of the main CMakeLists and paste it inside the CMakeLists.txt  
6. Change the name of the of the executable to any name you want in the main CMakeLists.txt in the package
   ```bash
   set (MAIN_EXECUTABLE_NAME Any_name_you_want)
   ```
Finally Enjoy your distributed ros2 cpp project easily
# Illustration Video

