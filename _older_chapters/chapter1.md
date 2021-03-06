---
title       : Basics of R Programming
description : In this Section we will begin to explore R and learn how it handles data. We will focus on major data types that we use frequently in statistics and the basics of how we use them. As we move forward these data types will be key to analyzing statistics.  
attachments :


--- type:VideoExercise lang:r xp:25 skills:1   key:1ee3f6290a
## Getting Start in R

*** =video_link

//player.vimeo.com/video/168224745





--- type:NormalExercise lang:r xp:100 skills:1 key:e412be26b2
##Practicing Basic R

*** =instructions
You can run R code with this. Place the solution under the commented section and hit run.

*** =hint

Here is a hint: use `<-` for assignment

*** =sample_code

```{r}
# Create a variable a, equal to 5


# Square a

```

*** =solution

```{r}
# Create a variable a, equal to 5
a <- 5

# Square a
a^2
```

*** =sct
```{r}
test_object("a")
test_output_contains("25", incorrect_msg = "Make sure to print `a`")
success_msg("Great!")
```


--- type:VideoExercise lang:r xp:25 skills:1   key:7fb790f570
## Simple Procedures in R

*** =video_link

//player.vimeo.com/video/168226884



--- type:NormalExercise lang:r xp:100 skills:1 key:5a54b078aa

## Basic Procedures in R

*** =pre_exercise_code
```{r}
b <- NA
```

*** =sample_code

```{r}
# Create a variable b, equal to 4



# What is the log of b?


# what is the exponential of the log of b?

```

*** =solution

```{r}
# Create a variable b, equal to 4
b = 4


# What is the log of b?
 log(b)

# what is the exponential of the log of b?

exp(log(b))
```
*** =sct

```{r}
test_object("b")
test_function("log", args = "x") 
test_function("exp", args="x")
test_output_contains("1.386", incorrect_msg = "Did you take the logarithm of b?")
test_output_contains("4", incorrect_msg = "Did you take theexponential of the logarithm of b?")
test_error()
success_msg("Great job!")


```

--- type:VideoExercise lang:r xp:25 skills:1    key:d1e309b772
## Getting Help in R

*** =video_link

//player.vimeo.com/video/168234652



--- type:VideoExercise lang:r xp:25 skills:1    key:c1c4a17c89
## Data Objects in R

*** =video_link



//player.vimeo.com/video/168247352






--- type:MultipleChoiceExercise lang:r xp:25 skills:1  key:be0cd6ce2a

## Practicing with Data Objects in R


Consider the functions Below. What are the boolean values for them. 

```
#The First

0 == 4/3*3 - 4

The Second

all.equal(0, 4/3*3 - 4)
```


*** =instructions
- Both False
- Both True
- First False and Second True

- First True and Second True

*** =pre_exercise_code

```{r}
# no pec
```

*** =hint
If you cannot figure this out try and run them. 

*** =sct
```{r}
msg1 = "That is not correct!"
msg2 = "Exactly! "
msg3 = "Ask yourself if we perform an operation on anything of the numbers"
test_mc(correct=3, feedback_msg=c(msg1, msg3, msg2, msg3))
```





--- type:VideoExercise lang:r xp:25 skills:1 key:70f3f253f8
## Vectors in R

*** =video_link
//player.vimeo.com/video/168261729





--- type:NormalExercise lang:r  xp:75 skills:1 key:770d89a78d
## Vectors in R Exercise 1

This exercise will allow you to look further into vectors. 

*** =instructions
Use R to answer the following questions. 

1. What is the length of x?
2. How many values in your vector x are below 2?
3. How many values in your vector x are above 7?
4. How many values in your vector x are below 3 or above 8?


*** =hint
Use your knowledge of indexing and functions that return Booleans.

*** =pre_exercise_code
```{r}
#You will find out more about the runif command in a few weeks.
set.seed(1234)
x = runif(5000, 1, 8)
```

*** =sample_code
```{r}
# Do Not Print X as it is a long vector
# 1. What is the length of x?

# 2. How many values in your vector x are below 2?


# 3. How many values in your vector x are above 7?


# 4. How many values in your vector x are below 3 or above 8?


```

*** =solution
```{r}
# Do Not Print X as it is a long vector
# 1. What is the length of x?
length(x)

# 2. How many values in your vector x are below 2?
length(which(x<2))

# 3. How many values in your vector x are above 7?
length(which(x>7))

# 4. How many values in your vector x are below 3 or above 8?
length(which(x<3 | x>8))

```

*** =sct
```{r}
test_error()
test_output_contains("5000")
test_function("which", args="x")
test_output_contains("696")
test_function("which", args="x")
test_output_contains("729")
test_function("which", args="x")
test_output_contains("1411")
success_msg("Great Job")
```


--- type:NormalExercise lang:r  xp:75 skills:1  key:0cd0b2c4e3
## Vectors in R Exercise 2

This exercise will allow you to look further into vectors. 

*** =instructions
Use R to answer the following questions. Given `x` from before:

1. How many times does the value 2 occur?
2. What are the 3400th - 3402th elements in your vector?
3. What is the smallest value in x?
4. What is the largest value in x?



*** =hint
Use your knowledge of indexing and functions that return Booleans.

*** =pre_exercise_code
```{r}
#You will find out more about the runif command in a few weeks.
set.seed(1234)
x = runif(5000, 1, 8)
```

*** =sample_code
```{r}
# Do Not Print X as it is a long vector
# 1. How many times does the value 2 occur?



# 2. What are the 3400th - 3402th elements in your vector?


# 3. What is the smallest value in x?


# 4. What is the largest value in x?


```

*** =solution
```{r}
# Do Not Print X as it is a long vector
# 1. How many times does the value 2 occur?
length(which(x==2))


# 2. What are the 3400th - 3402th elements in your vector?
x[3400:3402]

# 3. What is the smallest value in x?
min(x)

# 4. What is the largest value in x?
max(x)

```

*** =sct
```{r}
test_error()
test_function("length", args="x")
test_function("which", args="x")
test_output_contains("0") 
test_output_contains("x[3400:3402]")
test_output_contains("1.002393")
test_output_contains("7.99")
success_msg("Great Job")
```


//player.vimeo.com/video/168261729

--- type:VideoExercise lang:r xp:25 skills:1      key:fb0dfd78e7
## Arrays in R

*** =video_link
//player.vimeo.com/video/168265628


--- type:VideoExercise lang:r xp:25 skills:1      key:bb2242f8de
## Matrices in R

*** =video_link

//player.vimeo.com/video/168271916


--- type:NormalExercise lang:r  xp:75 skills:1   key:2c0f7cc31b
## Matrices in R Practice

This exercise will allow you to explore Matrices. 

*** =instructions
Use R to complete the tasks on the right and answer the following questions. 

1. Find the row sums of c. 
2. Find the column sums of c. 
3. What is the value of the 3rd column and 98th row?


*** =hint
Use your knowledge of Matrices to answer these questions. 

*** =pre_exercise_code
```{r}
#You will find out more about the runif command in a few weeks.
set.seed(1234)
x = runif(5000, 1, 8)
```

*** =sample_code
```{r}
# Do Not Print X as it is a long vector
# Create a matrix of x with 100 columns and fill it by row
# Label this matrix c


# 1. Find the row means of c. 


# 2. Find the column means of c. 


# 3. What is the value of the 3rd column and 98th row?


```

*** =solution
```{r}
# Do Not Print X as it is a long vector
# Create a matrix of x with 100 columns and fill it by row
# Label this matrix c
c <- matrix(x, ncol=100, byrow=TRUE)

# 1. Find the row means of c. 
apply(c, 1, mean)


# 2. Find the column means of c. 
apply(c, 2, mean)

# 3. What is the value of the 3rd column and 98th row?
c[3,98]
```

*** =sct
```{r}
test_error()
test_correct({
test_object("c")
}, {
  test_function("matrix", args = "byrow") 
})
test_correct({
test_object("c")
}, {
  test_function("matrix", args = "ncol") 
})
test_function("apply")
test_output_contains("4.062481")
test_function("apply")
test_output_contains("4.058472")
test_output_contains("1.80")
success_msg("Great Job")
```







--- type:VideoExercise lang:r xp:25 skills:1      key:7317839f79
## Lists in R

*** =video_link



//player.vimeo.com/video/168275483





--- type:NormalExercise lang:r  xp:75 skills:1 key:b5d6c5160e
## Lists in R Practice

This exercise will allow you to explore lists.  A simple Regression has been stored for you it is called `model`.

*** =instructions
Use R to complete the tasks on the right.


*** =hint
Use your knowledge of lists to answer these questions. 

*** =pre_exercise_code
```{r}
set.seed(1234)
x = rnorm(500, 10, 3)
y = runif(1)*x + rnorm(500,0,3.4)
model = lm(y~x)
```

*** =sample_code
```{r}
# 1. Find the summary of model and assign it as summary. 


# 2.  What does list summary contain?



# 2. Extract the coefficients summary and assign this as coeff. 



# 3. Print coeff.


# 4. What is the class of coeff?


# 5. From coeff extract the column of p-values. 



```

*** =solution
```{r}

# 1. Find the summary of model and assign it as summary. 
summary = summary(model)

# 2.  What does list summary contain?

names(summary)

# 2. Extract the coefficients summary and assign this as coeff. 

coeff = summary$coefficients

# 3. Print coeff.

coeff


# 4. What is the class of coeff?
typeof(coeff)

# 5. From coeff extract the column of p-values. 

coeff[,4]


```

*** =sct
```{r}
test_error()
test_correct({
test_object("summary")
}, {
  test_function("summary") 
})
test_function("names")
test_object("coeff")
test_function("typeof")
test_output_contains("coeff[,4]")
success_msg("Great Job")
```





--- type:VideoExercise lang:r xp:25 skills:1      key:55e8de92d3
## Dataframes in R

*** =video_link



//player.vimeo.com/video/168861291



--- type:NormalExercise lang:r  xp:75 skills:1   key:b9a2b5d65d
## Dataframes in R Practice

This exercise will allow you to explore dataframes.  A dataframe has been stored for you called `example`.

*** =instructions
Use R to complete the tasks on the right.


*** =hint
Use your knowledge of dataframes to answer these questions. 

*** =pre_exercise_code
```{r}
set.seed(1234)
example = data.frame(c1=runif(50), c2=rnorm(50), c3=runif(50))
```

*** =sample_code
```{r}
# 1.  How many observations are there in example? 



# 2. How many variables are there in example? 



# 3. What are the names of the variables in example?



# 4.  Create a dataframe with only observations where c1 > 0.2? Name this c1_gr_02.



# 5.  Create a dataframe with only observations where c1 > 0.2 and c2 > 0.2? Name this c1_c2_gr_02.


```

*** =solution
```{r}

# 1.  How many observations are there in example? 

dim(example)[1]

# 2. How many variables are there in example? 

dim(example)[2]

# 3. What are the names of the variables in example?

names(example)

# 4.  Create a dataframe with only observations where c1 > 0.2? Name this c1_gr_02.

c1_gr_02 <- example[example$c1>0.2,]

# 5.  Create a dataframe with only observations where c1 > 0.2 and c2 > 0.2? Name this c1_c2_gr_02.

c1_c2_gr_02 <- example[example$c1>0.2 & example$c2>0.2,]



```

*** =sct
```{r}
test_error()
test_function("dim")
test_function("dim")
test_function("names")
test_object("c1_gr_02", incorrect_msg = "Did you remember to name the new dataframe?")
test_object("c1_c2_gr_02",  incorrect_msg = "Did you remember to name the new dataframe?")
success_msg("Great Job")
```



