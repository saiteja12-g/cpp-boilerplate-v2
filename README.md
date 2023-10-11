# Valgrind Exercise

 ### [Sai Teja Gilukara](https://github.com/saiteja12-g) 
 ### Email id: saitejag@umd.edu  
 ### UID: 119369623

## Instructions to run the program locally

## Standard install and build via command-line
```
git clone -b valgrind_exercise --recursive https://github.com/saiteja12-g/cpp-boilerplate-v2.git
cd cpp-boilerplate-v2/
cmake -S ./ -B build/
cmake --build build/
./build/app/shell-app
```

## Run valgrind
```
valgrind --leak-check=full ./build/app/shell-app
```

## Kcachegrind Memory Profile Output
```
valgrind --tool=callgrind ./build/app/shell-app
kcachegrind
```
open the file callgrid.out.xxxx
### Identified Errors 
![Valgrind terminal output](<results/identified errors using valgrind.png>)

### After Fixing Errors
![Alt text](<results/fixed valgrind errors.png>)

### Cache Profile
![Alt text](<results/callgrind.png>)

## Extra Credits

What happens when the executable is linked statically?  Does Valgrind still detect those same bugs? Why or why not.

*Answer:*   
When an executable is linked statically, the linker copies the code for all of the libraries that the executable depends on into the executable itself. This means that the executable does not need to load any shared libraries at runtime.  
Valgrind can still detect bugs in statically linked executables but it needs to intercept and monitor system calls made by executables.  
*Valgrind may not be able to detect all bugs in statically linked executables. For example, Valgrind cannot detect bugs that occur in the initialization or termination code of the executable.*