# Homework #2
Cynthia I. Rodriguez
## Exercise 1
Ask a question that requires a student to understand navigation and manipulation of directories in a filesystem. Your question should require an answer using at least the following commands/concepts: cd, ../, mkdir, rmdir

### Instructions for undergraduate:
> Please create a directory in your home directory with the name of your project and create the following subdirectories: data, temporary, protocols, and final.

### ANSWER:
``` 
mkdir /homedirectory/myproject
mkdir /homedirectory/myproject/data
mkdir /homedirectory/myproject/temporary
mkdir /homedirectory/myproject/protocols
mkdir /homedirectory/myproject/final
```
### Instructions for undergraduate:
> Go into your project directory and once inside delete the subdirectory called "protocols".
```
cd  /homedirectory/myproject
rmdir protocols
```
### Instructions for undergraduate:
> Back up to the home directory and create a new directory called experiments
### ANSWER:
```
cd ../
mkdir experiments
```
### Question 1 Comments:
This was very well done, the only issue is that anytime you specify "/" before anything while traversing or modifying directories, you are stating to start in the root directory, which is typically a big nono and can lead to massive system failure if you are the owner of the linux computer. typically you want to do ~ or use / when you are indeed accessing the directory (this is using the full path). It is generally recommended to not use full paths but instead relational paths from within your current working directory. i.e. if you are in /homedirectory and you want to create /homedirectory/class you would simply do mkdir class while working in the /homedirectory. This also makes code much more reusable as you do not have to constantly update static paths in your scripts when reusing them, and instead can be used in any working directory as long as the directory where the copy of your script is located, contains the required files for it to run on.


## Exercise 2
Ask a question that requires a student to understand the difference between accessing a column in a matrix with numeric indices versus accessing a column in a data frame with numeric indices. Your question should require an answer comparing the following: mymatrix[,1] vs. mydf[,1] vs. mydf[1] vs. mydf[[1]].

### Instructions for undergraduate:
> Please create a matrix in R that has 4 columns and 3 rows with the numbers 1 through 12. The numbers should go down per columns. Then visualize the data matrix.

### ANSWER:
```
mymatrix <- matrix(data = 1:12, nrow = 3, ncol = 4)
mymatrix
      [,1] [,2] [,3] [,4]
[1,]    1    4    7   10
[2,]    2    5    8   11
[3,]    3    6    9   12
```
### Instructions for undergraduate:
>Subset data from the matrix by getting only the first column of such matrix as a vector:
### ANSWER:
```
> mymatrix[,1]
[1] 1 2 3
```
### Instructions for undergraduate:
>Now subset only the 3rd value of the matrix:
### ANSWER:
```
> mymatrix[3]
[1] 3
```
### Instructions for undergraduate:
>Subset the same value with a different command:
### ANSWER:
```
> mymatrix[[3]]
[1] 3
```
### Instructions for undergraduate:
> Now load the following dataframe into RStudio (from csv format) and visualize your dataframe:
```
Name	Age	Color
Laura	10	green
Paco	12	blue
Tony	11	yellow
Jen	  16	pink
```
### ANSWER:
```
mydf <-read.csv('mydf.csv')
mydf
```
### Instructions for undergraduate:
> Now try the same commands you performed for the matrix on this dataframe and explain what are the differences you obtain:
### ANSWER:
```
> mydf[,1]
[1] Laura Paco  Tony  Jen  
Levels: Jen Laura Paco Tony
#The characters of the first column get converted into a factors (numbers)- it has stored the factor information as a vector.

> mydf[3]
   color
1  green
2   blue
3 yellow
4   pink
#Running this command on the matrix subsetted only the 3rd value of the matrix; however, when you run the same command on the dataframe it gets you the 3rd column of the dataframe.

> mydf[[3]]
[1] green  blue   yellow pink  
Levels: blue green pink yellow
#Running this command on the matrix subsetted only the 3rd value of the matrix; however, when you run the same command on the dataframe it gets you the 3rd column of the dataframe as a vector.
```

## Exercise 3
Ask a question that requires a student to understand how to share access to a directory and a file in that directory on a Unix/Linux filesystem from their home directory with a colleague without exposing the user's entire directory. Your question should require an answer using chmod {u,g,o}{+,-}{r,w,x} (not using octal permissions).

### Instructions for undergraduate:
You need to share access to a folder named bacteria within your home directory with a colleague and one of its files named microbes. Make sure you do not share the entire directory's contents. Make sure your collegue can access the file and see it but cannot modify it.
### ANSWER:
```
chmod o+x /homedirectory
chmod o+x /homedirectory/bacteria
cd home/bacteria
chmod o+r microbes
#OR instead of entering the directory "bacteria" you can grant access directly by listing the whole path to the file:
chmod o+r /homedirectory/bacteria/microbes
```
###Question 3 Comments:
This is done very well and I like how you discuss how it is also necessary for all parent directories to have user read access in order for the user to read the file. It is also important that the directories also have execute access. Also for this specific case you can do away with the o and just do chmod +rx microbes in order to do the same thing but in one step. This gives a blanket access of read and write. The additional option allows you to specify if you want to give group access but not all user access. Sometimes this is also necessary, depending on your realworld application. Great job!
